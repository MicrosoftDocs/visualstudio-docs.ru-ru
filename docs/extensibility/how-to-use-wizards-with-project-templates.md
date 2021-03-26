---
title: Практическое руководство. Использование мастеров для шаблонов проекта
description: Узнайте, как использовать интерфейс Ивизард в пакете SDK для Visual Studio, который позволяет запускать пользовательский код, когда пользователь создает проект на основе шаблона.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- project templates [Visual Studio], wizards
- Visual Studio templates, wizards
- wizards [Visual Studio], project templates
- templates [Visual Studio], wizards
- IWizard interface
ms.assetid: 47ee26cf-67b7-4ff1-8a9d-ab11a725405c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 41290f946c198ed854cad9a7eb2af088f6fe228a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082287"
---
# <a name="how-to-use-wizards-with-project-templates"></a>Руководство. Использование мастеров с шаблонами проектов

Visual Studio предоставляет <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> интерфейс, который при реализации позволяет запускать пользовательский код, когда пользователь создает проект на основе шаблона.

Настройку шаблона проекта можно использовать для вывода пользовательского интерфейса, который собирает ввод пользователя для настройки шаблона, добавления дополнительных файлов в шаблон или любых других действий, разрешенных в проекте.

<xref:Microsoft.VisualStudio.TemplateWizard.IWizard>Методы интерфейса вызываются в различные моменты времени при создании проекта, начиная с момента нажатия пользователем кнопки **ОК** в диалоговом окне **Новый проект** . Каждый метод интерфейса именуется для описания точки, в которой он вызывается. Например, Visual Studio вызывает <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> немедленно при начале создания проекта, что делает его хорошим местом для написания пользовательского кода для получения данных, вводимых пользователем.

## <a name="create-a-project-template-project-with-a-vsix-project"></a>Создание проекта шаблона проекта с помощью проекта VSIX

Вы начинаете создавать пользовательский шаблон с помощью проекта шаблона проекта, который является частью пакета SDK для Visual Studio. В этой процедуре мы будем использовать проект шаблона проекта C#, но также Visual Basic проект шаблона проекта. Затем добавьте проект VSIX в решение, содержащее проект шаблона проекта.

1. Создайте проект шаблона проекта C# (в Visual Studio выберите **файл**  >  **создать**  >  **проект** и выполните поиск по запросу "шаблон проекта"). Назовите его **MyProjectTemplate**.

   > [!NOTE]
   > Возможно, вам будет предложено установить пакет SDK для Visual Studio. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

2. Добавьте новый проект VSIX в то же решение, что и проект шаблона проекта (в **Обозреватель решений** выберите узел решения, щелкните правой кнопкой мыши и выберите **Добавить**  >  **Новый проект** и выполните поиск по запросу VSIX). Назовите его **мипрожектвизард.**

3. Задайте проект VSIX в качестве запускаемого проекта. В **Обозреватель решений** выберите узел проекта VSIX, щелкните его правой кнопкой мыши и выберите пункт **Назначить запускаемым проектом**.

4. Добавьте проект шаблона в качестве ресурса для проекта VSIX. В **Обозреватель решений** в узле VSIX Project найдите файл *source. extension. vsixmanifest* . Дважды щелкните его, чтобы открыть в редакторе манифеста.

5. В редакторе манифеста выберите вкладку **активы** в левой части окна.

6. На вкладке **активы** выберите **создать**. В окне **Добавление нового актива** для поля Тип выберите **Microsoft. VisualStudio. ProjectTemplate**. В поле **источник** выберите **проект в текущем решении**. В поле **проект** выберите **MyProjectTemplate**. Нажмите кнопку **ОК**.

7. Постройте решение и запустите отладку. Откроется второй экземпляр Visual Studio. Это может занять несколько минут.

8. Во втором экземпляре Visual Studio попробуйте создать новый проект с новым шаблоном (**файл**  >  **создать**  >  **проект**, выполните поиск по слову «MyProject»). Новый проект должен появиться с классом с именем **Class1**. Теперь вы создали пользовательский шаблон проекта. Теперь отключите отладку.

## <a name="create-a-custom-template-wizard"></a>Мастер создания настраиваемых шаблонов

В этой процедуре показано, как создать настраиваемый мастер, открывающий форму Windows Forms до создания проекта. Форма позволяет пользователям добавлять значение настраиваемого параметра, которое добавляется в исходный код во время создания проекта.

1. Настройте проект VSIX, чтобы разрешить ему создание сборки.

2. В **Обозреватель решений** выберите узел проекта VSIX. Ниже **Обозреватель решений**, вы увидите окно **свойства** . В противном случае выберите **вид**  >  **окно свойств** или нажмите клавишу **F4**. В окне **Свойства** выберите следующие поля `true` :

   - **Включить сборку в контейнер VSIX**

   - **Включить отладочные символы в контейнер VSIX**

   - **Включить отладочные символы в локальное развертывание VSIX**

3. Добавьте сборку в качестве ресурса в проект VSIX. Откройте файл *source. extension. vsixmanifest* и перейдите на вкладку **активы** . В окне **Добавление нового актива** в поле **Тип** выберите **Microsoft. VisualStudio. Assembly**, в поле **источник** выберите **проект в текущем решении**, а для **проекта** выберите **мипрожектвизард**.

4. Добавьте следующие ссылки в проект VSIX. (В **Обозреватель решений** в узле VSIX-проект выберите **ссылки**, щелкните правой кнопкой мыши и выберите команду **Добавить ссылку**.) В диалоговом окне **Добавление ссылки** на вкладке **платформа** найдите сборку **System. Windows Forms** и выберите ее. Также найдите и выберите сборки **System** и **System. Drawing** . Теперь перейдите на вкладку **расширения** . Найдите сборку **EnvDTE** и выберите ее. Также Найдите сборку **Microsoft. VisualStudio. темплатевизардинтерфаце** и выберите ее. Нажмите кнопку **ОК**.

5. Добавьте класс для реализации мастера в проект VSIX. (В **Обозреватель решений** щелкните правой кнопкой мыши узел проекта VSIX и выберите **Добавить**, затем **новый элемент**, затем **класс**.) Назовите класс **визардимплементатион**.

6. Замените код в файле *визардимплементатионкласс. CS* следующим кодом:

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.TemplateWizard;
   using System.Windows.Forms;
   using EnvDTE;

   namespace MyProjectWizard
   {
       public class WizardImplementation:IWizard
       {
           private UserInputForm inputForm;
           private string customMessage;

           // This method is called before opening any item that
           // has the OpenInEditor attribute.
           public void BeforeOpeningFile(ProjectItem projectItem)
           {
           }

           public void ProjectFinishedGenerating(Project project)
           {
           }

           // This method is only called for item templates,
           // not for project templates.
           public void ProjectItemFinishedGenerating(ProjectItem
               projectItem)
           {
           }

           // This method is called after the project is created.
           public void RunFinished()
           {
           }

           public void RunStarted(object automationObject,
               Dictionary<string, string> replacementsDictionary,
               WizardRunKind runKind, object[] customParams)
           {
               try
               {
                   // Display a form to the user. The form collects
                   // input for the custom message.
                   inputForm = new UserInputForm();
                   inputForm.ShowDialog();

                   customMessage = UserInputForm.CustomMessage;

                   // Add custom parameters.
                   replacementsDictionary.Add("$custommessage$",
                       customMessage);
               }
               catch (Exception ex)
               {
                   MessageBox.Show(ex.ToString());
               }
           }

           // This method is only called for item templates,
           // not for project templates.
           public bool ShouldAddProjectItem(string filePath)
           {
               return true;
           }
       }
   }
   ```

    **Усеринпутформ** , на который ссылается этот код, будет реализован позже.

    `WizardImplementation`Класс содержит реализации методов для каждого члена <xref:Microsoft.VisualStudio.TemplateWizard.IWizard> . В этом примере только <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A> метод выполняет задачу. Все остальные методы либо ничего не выполняют, либо возвращают `true` .

    <xref:Microsoft.VisualStudio.TemplateWizard.IWizard.RunStarted%2A>Метод принимает четыре параметра:

   - <xref:System.Object>Параметр, который можно привести к корневому <xref:EnvDTE._DTE> объекту, чтобы обеспечить возможность настройки проекта.

   - <xref:System.Collections.Generic.Dictionary%602>Параметр, содержащий коллекцию всех предварительно определенных параметров в шаблоне. Дополнительные сведения о параметрах шаблона см. в разделе [Параметры шаблона](../ide/template-parameters.md).

   - <xref:Microsoft.VisualStudio.TemplateWizard.WizardRunKind>Параметр, содержащий сведения о том, какой тип шаблона используется.

   - <xref:System.Object>Массив, содержащий набор параметров, передаваемых в мастер Visual Studio.

     В этом примере в параметр добавляется значение параметра из пользовательской формы ввода <xref:System.Collections.Generic.Dictionary%602> . Каждый экземпляр `$custommessage$` параметра в проекте будет заменен текстом, введенным пользователем.

7. Теперь создайте **усеринпутформ**. В файле *визардимплементатион. CS* добавьте следующий код после конца `WizardImplementation` класса.

   ```csharp
   public partial class UserInputForm : Form
       {
           private static string customMessage;
           private TextBox textBox1;
           private Button button1;

           public UserInputForm()
           {
               this.Size = new System.Drawing.Size(155, 265);

               button1 = new Button();
               button1.Location = new System.Drawing.Point(90, 25);
               button1.Size = new System.Drawing.Size(50, 25);
               button1.Click += button1_Click;
               this.Controls.Add(button1);

               textBox1 = new TextBox();
               textBox1.Location = new System.Drawing.Point(10, 25);
               textBox1.Size = new System.Drawing.Size(70, 20);
               this.Controls.Add(textBox1);
           }
           public static string CustomMessage
           {
               get
               {
                   return customMessage;
               }
               set
               {
                   customMessage = value;
               }
           }
           private void button1_Click(object sender, EventArgs e)
           {
               customMessage = textBox1.Text;
               this.Close();
           }
       }
   ```

    Форма ввода пользователя предоставляет простую форму для ввода настраиваемого параметра. Форма содержит текстовое поле с именем `textBox1` и кнопку с именем `button1` . При нажатии кнопки текст из текстового поля сохраняется в `customMessage` параметре.

## <a name="connect-the-wizard-to-the-custom-template"></a>Подключение мастера к пользовательскому шаблону

Чтобы пользовательский шаблон проекта мог использовать пользовательский мастер, необходимо подписать сборку мастера и добавить некоторые строки в пользовательский шаблон проекта, чтобы сообщить ему, где найти реализацию мастера при создании нового проекта.

1. Подпишите сборку. В **Обозреватель решений** выберите проект VSIX, щелкните его правой кнопкой мыши и выберите пункт **Свойства проекта**.

2. В окне **Свойства проекта** выберите вкладку **Подписывание** . на вкладке **Подписывание** установите флажок **подписать сборку**. В поле **выберите файл ключа строгого имени** выберите **\<New>** . В окне **Создание ключа строгого имени** в поле **имя файла ключа** введите **Key. snk**. Снимите флажок **защитить файл ключа с помощью поля пароля** .

3. В **Обозреватель решений** выберите проект VSIX и найдите окно **свойства** .

4. Установите **значение true** для поля **Копировать выходные данные сборки в выходной каталог** . Это позволяет копировать сборку в выходной каталог при перестроении решения. Он по-прежнему содержится в `.vsix` файле. Чтобы узнать ключ подписывания, необходимо просмотреть сборку.

5. Выполните повторную сборку решения.

6. Теперь файл key. snk можно найти в каталоге проекта Мипрожектвизард (*\<your disk location> \мипрожекттемплате\мипрожектвизард\кэй.СНК*). Скопируйте файл *Key. snk* .

7. Перейдите в выходной каталог и найдите сборку (*\<your disk location> \ MyProjectTemplate/MyProjectWizard\bin\Debug\MyProjectWizard.dll*). Вставьте здесь файл *Key. snk* . (Это не является абсолютно необходимым, но он упрощает следующие шаги.)

8. Откройте командное окно и перейдите в каталог, в котором была создана сборка.

9. Найдите средство подписи *sn.exe* . Например, в Windows 10 64-разрядной операционной системе типичный путь будет следующим:

     *C:\Program Files (x86) \Microsoft SDKs\Windows\v10.0A\bin\NETFX 4.6.1 Tools*

     Если средство не удается найти, попробуйте выполнить команду **WHERE/r. sn.exe** в командном окне. Запишите путь.

10. Извлеките открытый ключ из файла *Key. snk* . В окне команд введите

     **\<location of sn.exe>\sn.exe-p Key. SNK файл. key.**

     Не забудьте заключить путь *sn.exe* кавычками, если в именах каталогов есть пробелы.

11. Получите маркер открытого ключа из файла:

     **\<location of sn.exe>\sn.exe-t файл. key.**

     Опять же, не забудьте кавычки. В выходных данных должна отобразиться строка, подобная следующей:

     **Токен открытого ключа: \<token>**

     Запишите это значение.

12. Добавьте ссылку на пользовательский мастер в *VSTEMPLATE* файл шаблона проекта. В **Обозреватель решений** найдите файл с именем *MyProjectTemplate. vstemplate* и откройте его. После завершения \<TemplateContent> раздела добавьте следующий раздел:

    ```xml
    <WizardExtension>
        <Assembly>MyProjectWizard, Version=1.0.0.0, Culture=Neutral, PublicKeyToken=token</Assembly>
        <FullClassName>MyProjectWizard.WizardImplementation</FullClassName>
    </WizardExtension>
    ```

     Где **мипрожектвизард** — это имя сборки, а **Token** — маркер, скопированный на предыдущем шаге.

13. Сохраните все файлы в проекте и перестройте.

## <a name="add-the-custom-parameter-to-the-template"></a>Добавление пользовательского параметра в шаблон

В этом примере проект, используемый в качестве шаблона, отображает сообщение, указанное в форме пользовательского ввода пользовательского мастера.

1. В **Обозреватель решений** перейдите к проекту **MyProjectTemplate** и откройте *Class1. CS*.

2. В `Main` методе приложения добавьте следующую строку кода.

   ```csharp
   Console.WriteLine("$custommessage$");
   ```

    Параметр `$custommessage$` заменяется текстом, введенным в форме ввода пользователя при создании проекта на основе шаблона.

Ниже приведен полный файл кода, до его экспорта в шаблон.

```csharp
using System;
using System.Collections.Generic;
$if$ ($targetframeworkversion$ >= 3.5)using System.Linq;
$endif$using System.Text;

namespace $safeprojectname$
{
    public class Class1
    {
          static void Main(string[] args)
          {
               Console.WriteLine("$custommessage$");
          }
    }
}
```

## <a name="use-the-custom-wizard"></a>Использование настраиваемого мастера

Теперь можно создать проект на основе шаблона и использовать настраиваемый мастер.

1. Перестройте решение и начните отладку. Откроется второй экземпляр Visual Studio.

2. Создайте новый проект MyProjectTemplate. (**Файл**  >  **Новые**  >  **Проект**).

3. В диалоговом окне **Новый проект** найдите "MyProject", чтобы найти шаблон, введите имя и нажмите кнопку " **ОК**".

     Откроется форма ввода пользователя мастера.

4. Введите значение для пользовательского параметра и нажмите кнопку.

     Закрывается форма ввода пользователя мастера и проект создается на основе шаблона.

5. В **Обозреватель решений** щелкните правой кнопкой мыши файл исходного кода и выберите пункт **Просмотреть код**.

     Обратите внимание, что `$custommessage$` заменено текстом, введенным в форме пользовательского ввода мастера.

## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualStudio.TemplateWizard.IWizard>
- [Настройка шаблонов](../ide/customizing-project-and-item-templates.md)
- [Элемент Визардекстенсион (шаблоны Visual Studio)](../extensibility/wizardextension-element-visual-studio-templates.md)
- [Пакеты NuGet в шаблонах Visual Studio](/nuget/visual-studio-extensibility/visual-studio-templates)
