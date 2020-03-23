---
title: Attività UpdateManifestForBrowserApplication | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 079eecd6751f168a7beba32eda6d15eda712bd7f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631328"
---
# <a name="updatemanifestforbrowserapplication-task"></a>Attività UpdateManifestForBrowserApplication

L'attività <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> viene eseguita per aggiungere l'elemento ** \<hostInBrowser />** al manifesto dell'applicazione (*\<nomeprogetto>.exe.manifest*) quando viene compilato un progetto di applicazione browser XAML (XBAP).

## <a name="task-parameters"></a>Parametri dell'attività

|Parametro|Descrizione|
|---------------|-----------------|
|`ApplicationManifest`|Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica il percorso e il nome del file manifesto dell'applicazione a cui si desidera aggiungere l'elemento `<hostInBrowser />`.|
|`HostInBrowser`|Parametro **Boolean** obbligatorio.<br /><br /> Specifica se modificare il manifesto dell'applicazione per includere l'elemento ** \<hostInBrowser />.** Se **true**, un nuovo elemento **\<hostInBrowser />** viene incluso nell'elemento **\<entryPoint />**. L'inclusione dell'elemento è cumulativa: se un ** \<elemento hostInBrowser />** esiste già, non viene rimosso o sovrascritto. Al contrario, viene creato un elemento ** \<hostInBrowser />** aggiuntivo. Se è **false**, il manifesto dell'applicazione non viene modificato.|

## <a name="remarks"></a>Osservazioni

 Le applicazioni XBAP vengono eseguite tramite la distribuzione ClickOnce, pertanto devono essere pubblicate con la distribuzione di supporto e i manifesti dell'applicazione. MSBuild usa l'attività [GenerateApplicationManifest](generateapplicationmanifest-task.md) per generare un manifesto dell'applicazione.

 Quindi, per configurare un'applicazione da ospitare da un browser, è necessario aggiungere un elemento ** \<hostInBrowser />** aggiuntivo al manifesto dell'applicazione, come illustrato nell'esempio seguente:Then, to configure an application to be hosted from a browser, an additional hostInBrowser />element must be added to the application manifest, as shown in the following example:

```xml
<!--MyXBAPApplication.exe.manifest-->
<?xml version="1.0" encoding="utf-8"?>
<asmv1:assembly ... >
    <asmv1:assemblyIdentity ... />
    <application />
    <entryPoint>
      ...
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />
    </entryPoint>
  ...
/>
```

 L'attività <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> viene eseguita quando viene compilato un `<hostInBrowser />` progetto XBAP per aggiungere l'elemento.

## <a name="example"></a>Esempio

 L'esempio seguente illustra come verificare che l'elemento `<hostInBrowser />` sia incluso in un file manifesto dell'applicazione.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="UpdateManifestForBrowserApplicationTask">
    <UpdateManifestForBrowserApplication
      ApplicationManifest="MyXBAPApplication.exe.manifest"
      HostInBrowser="true" />
  </Target>
</Project>
```

## <a name="see-also"></a>Vedere anche

- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Riferimento alle attività](../msbuild/wpf-msbuild-task-reference.md)
- [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)
- [Riferimento alle attività](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Panoramica delle applicazioni browser XAML di WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)