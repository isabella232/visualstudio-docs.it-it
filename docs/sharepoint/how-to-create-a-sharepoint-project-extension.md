---
title: "Procedura: Creare un'SharePoint Project di estensione | Microsoft Docs"
description: Informazioni su come creare un'estensione di progetto in modo da poter aggiungere funzionalità SharePoint progetto aperto in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/28/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 9c70044b4a15bd0058a8bfb63ddcff44c149937d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131040"
---
# <a name="how-to-create-a-sharepoint-project-extension"></a>Procedura: Creare un'estensione SharePoint progetto
  Creare un'estensione di progetto quando si vuole aggiungere funzionalità a SharePoint progetto aperto in Visual Studio. Per altre informazioni, vedere [Estendere il SharePoint del progetto.](../sharepoint/extending-the-sharepoint-project-system.md)

### <a name="to-create-a-project-extension"></a>Per creare un'estensione di progetto

1. Creare un progetto Libreria di classi.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    - Microsoft.VisualStudio. SharePoint

    - System.ComponentModel.Composition

3. Creare una classe che implementi l'interfaccia <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>.

4. Aggiungere <xref:System.ComponentModel.Composition.ExportAttribute> alla classe . Questo attributo consente Visual Studio individuare e caricare <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> l'implementazione. Passare il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> tipo al costruttore dell'attributo.

5. Nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> metodo usare i membri del parametro *projectService* per definire il comportamento dell'estensione. Questo parametro è un <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> oggetto che fornisce l'accesso agli eventi definiti <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> nell'interfaccia .

## <a name="example"></a>Esempio
 Nell'esempio di codice seguente viene illustrato come creare una semplice estensione di progetto che gestisce la maggior parte degli eventi SharePoint progetto definiti <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> dall'interfaccia . Per testare il codice, creare un progetto SharePoint in e quindi aggiungere altri progetti alla soluzione, modificare i valori delle proprietà del progetto oppure eliminare o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] escludere un progetto. L'estensione notifica gli eventi scrivendo messaggi nella finestra **Output** e nella **finestra Elenco** errori.

  ```vb
    Imports Microsoft.VisualStudio.SharePoint
    Imports System.ComponentModel
    Imports System.ComponentModel.Composition

    Namespace Contoso.ExampleProjectExtension
      <Export(GetType(ISharePointProjectExtension))> _
      Class ExampleProjectExtension
        Implements ISharePointProjectExtension

        Private WithEvents projectService As ISharePointProjectService

        Public Sub Initialize(ByVal projectService As ISharePointProjectService) _
            Implements ISharePointProjectExtension.Initialize
            Me.projectService = projectService
        End Sub

        ' A project was added.
        Private Sub projectService_ProjectAdded(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectAdded
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was added: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was loaded in the IDE.
        Private Sub projectService_ProjectInitialized(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectInitialized
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being initialized: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' The name of a property was changed.
        Private Sub projectService_ProjectNameChanged(ByVal sender As Object, ByVal e As NameChangedEventArgs) _
            Handles projectService.ProjectNameChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project property value was changed.
        Private Sub ProjectPropertyChanged(ByVal sender As Object, ByVal e As PropertyChangedEventArgs) _
            Handles projectService.ProjectPropertyChanged
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project is being removed or unloaded.
        Private Sub projectService_ProjectRemoved(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectRemoved
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub

        ' A project was removed or unloaded.
        Private Sub projectService_ProjectDisposing(ByVal sender As Object, ByVal e As SharePointProjectEventArgs) _
            Handles projectService.ProjectDisposing
            Dim project As ISharePointProject = CType(sender, ISharePointProject)
            Dim message As String = String.Format("The following project was removed or unloaded: {0}", e.Project.Name)
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message)
        End Sub
      End Class
    End Namespace
    ```

    ```csharp
    using Microsoft.VisualStudio.SharePoint;
    using System;
    using System.ComponentModel;
    using System.ComponentModel.Composition;

    namespace Contoso.ExampleProjectExtension
    {
      [Export(typeof(ISharePointProjectExtension))]
      internal class ExampleProjectExtension : ISharePointProjectExtension
      {
        public void Initialize(ISharePointProjectService projectService)
        {
            projectService.ProjectAdded += projectService_ProjectAdded;
            projectService.ProjectInitialized += projectService_ProjectInitialized;
            projectService.ProjectNameChanged += projectService_ProjectNameChanged;
            projectService.ProjectPropertyChanged += projectService_ProjectPropertyChanged;
            projectService.ProjectRemoved += projectService_ProjectRemoved;
            projectService.ProjectDisposing += projectService_ProjectDisposing;
        }

        // A project was added.
        void projectService_ProjectAdded(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was added: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is loaded in the IDE.
        void projectService_ProjectInitialized(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being initialized: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // The name of a project was changed.
        void projectService_ProjectNameChanged(object sender, NameChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The project named {0} was changed to {1}.", e.OldName, project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project property value was changed.
        private void projectService_ProjectPropertyChanged(object sender, PropertyChangedEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following property of the {0} project was changed: {1}",
                project.Name, e.PropertyName);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project is being removed or unloaded.
        void projectService_ProjectRemoved(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project is being removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }

        // A project was removed or unloaded.
        void projectService_ProjectDisposing(object sender, SharePointProjectEventArgs e)
        {
            ISharePointProject project = (ISharePointProject)sender;
            string message = String.Format("The following project was removed or unloaded: {0}", e.Project.Name);
            project.ProjectService.Logger.WriteLine(message, LogCategory.Message);
        }
     }
  }
  ```

Questo esempio usa il SharePoint servizio di progetto per scrivere il messaggio nella finestra **Output** e nella **finestra Elenco** errori. Per altre informazioni, vedere [Usare il SharePoint servizio di progetto](../sharepoint/using-the-sharepoint-project-service.md).

 Per esempi che illustrano come gestire gli eventi e , vedere Procedura: Aggiungere una voce di menu di scelta rapida a progetti SharePoint e Procedura: Aggiungere una proprietà <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectMenuItemsRequested> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectPropertiesRequested> a SharePoint [progetti](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md). [](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio richiede riferimenti agli assembly seguenti:

- Microsoft.VisualStudio. SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Distribuzione dell'estensione
 Per distribuire l'estensione, creare un pacchetto di estensione (VSIX) per l'assembly e qualsiasi altro file che [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] si vuole distribuire con l'estensione. Per altre informazioni, vedere [Deploy Extensions for the SharePoint tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Vedi anche
- [Estendere il SharePoint del progetto](../sharepoint/extending-the-sharepoint-project-system.md)
- [Procedura: Aggiungere una voce di menu di scelta rapida SharePoint progetti](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Procedura: Aggiungere una proprietà a SharePoint progetti](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Procedura dettagliata: Creare un'estensione SharePoint progetto](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
