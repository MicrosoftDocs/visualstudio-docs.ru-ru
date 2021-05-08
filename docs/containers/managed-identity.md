---
title: Использование управляемого удостоверения с Bridge to Kubernetes
ms.technology: vs-azure
ms.date: 04/28/2021
ms.topic: conceptual
description: Узнайте, как использовать управляемое удостоверение Azure Active Directory (Azure AD) в кластере AKS с Bridge to Kubernetes
monikerRange: '>=vs-2019'
manager: jmartens
author: ghogen
ms.author: ghogen
ms.openlocfilehash: e4847b25531b48c8200a2620ca3e975f9677c881
ms.sourcegitcommit: 60b7a6159045a44293043a519c8ea6d915bf2c31
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/01/2021
ms.locfileid: "108335105"
---
# <a name="use-managed-identity-with-bridge-to-kubernetes"></a>Использование управляемого удостоверения с Bridge to Kubernetes

Если кластер AKS использует функции безопасности [управляемого удостоверения](/azure/active-directory/managed-identities-azure-resources/overview) для безопасного доступа к секретам и ресурсам, для Bridge to Kubernetes требуется специальная настройка, чтобы обеспечить возможность работы с этими функциями. На локальный компьютер необходимо загрузить маркер Azure Active Directory (AD), чтобы обеспечить надлежащую защиту выполнения и отладки в локальной среде, а для этого требуется специальная настройка Bridge to Kubernetes. В этой статье показано, как настроить Bridge to Kubernetes для работы со службами, использующими управляемое удостоверение.

## <a name="how-to-configure-your-service-to-use-managed-identity"></a>Настройка службы для использования управляемого удостоверения

Чтобы включить локальный компьютер с поддержкой управляемого удостоверения, в файле *KubernetesLocalConfig.yaml* в разделе `enableFeatures` добавьте `ManagedIdentity`. Добавьте раздел `enableFeatures`, если он еще не создан.

```yaml
enableFeatures:
    ManagedIdentity
```

> [!WARNING]
> Используйте управляемое удостоверение для Bridge to Kubernetes только с кластерами разработки, а не с рабочими кластерами, так как маркер Azure AD размещается на локальном компьютере, что представляет потенциальную угрозу безопасности.

Если у вас нет файла *KubernetesLocalConfig.yaml*, его можно создать: см. раздел [Настройка Bridge to Kubernetes](configure-bridge-to-kubernetes.md).

## <a name="how-to-fetch-the-azure-active-directory-tokens"></a>Получение маркеров Azure Active Directory

Необходимо убедиться, что вы используете <xref:Azure.Identity.DefaultAzureCredential> или <xref:Azure.Identity.ManagedIdentityCredential> в коде при получении маркера.

В следующем коде C# показано, как получить учетные данные учетной записи хранения при использовании `ManagedIdentityCredential`:

```csharp
var credential = new ManagedIdentityCredential(miClientId);
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

В следующем коде показано, как получить учетные данные учетной записи хранения при использовании DefaultAzureCredential:

```csharp
var credential = new DefaultAzureCredential();
Console.WriteLine("Created credential");
var containerClient = new BlobContainerClient(new Uri($"https://{accountName}.blob.windows.net/{containerName}"), credential);
Console.WriteLine("Created blob client");
```

Сведения о том, как получить доступ к другим ресурсам Azure с помощью управляемого удостоверения, см. в разделе [Дальнейшие действия](#next-steps).

## <a name="receive-azure-alerts-when-tokens-are-downloaded"></a>Получение оповещений Azure при загрузка маркеров

Всякий раз, когда Bridge to Kubernetes используется со службой, маркер Azure AD загружается на локальный компьютер. Чтобы получать уведомления, когда это происходит, вы можете включить оповещения Azure. Дополнительные сведения см. в статье [Включение Azure Defender](/azure/security-center/enable-azure-defender). Имейте в виду, что плата взимается по истечении 30-дневного пробного периода.

## <a name="next-steps"></a>Дальнейшие действия

Теперь, когда Bridge to Kubernetes настроен для работы с кластером AKS, использующим управляемое удостоверение, можно выполнить отладку в нормальном режиме. См. раздел [bridge-to-kubernetes.md#connect-to-your-cluster-and-debug-a-service].

Дополнительные сведения об использовании управляемого удостоверения для доступа к ресурсам Azure см. в следующих руководствах:

- [Руководство по Использование назначаемого системой управляемого удостоверения на виртуальной машине Linux для доступа к службе хранилища Azure](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-storage)
- [Руководство по Использование назначаемого системой управляемого удостоверения на виртуальной машине Linux для доступа к Azure Data Lake Storage](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-datalake)
- [Руководство по Использование назначаемого системой управляемого удостоверения на виртуальной машине Linux для доступа к Azure Key Vault](/azure/active-directory/managed-identities-azure-resources/tutorial-linux-vm-access-nonaad)

В этом разделе также приводятся другие руководства по использованию управляемого удостоверения для доступа к другим ресурсам Azure.

## <a name="see-also"></a>См. также

[Azure Active Directory](/azure/active-directory/managed-identities-azure-resources/)
