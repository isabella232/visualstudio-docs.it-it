---
title: Attività UpdateManifestForBrowserApplication | Microsoft Docs
description: Informazioni su come MSBuild esegue l'attività UpdateManifestForBrowserApplication per aggiungere l'elemento hostInBrowser al manifesto dell'applicazione.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9e71e11988d4dd853b0f97c745b6d720a45adcdc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961547"
---
# <a name="updatemanifestforbrowserapplication-task"></a>Attività UpdateManifestForBrowserApplication

L' <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> attività viene eseguita per aggiungere l' **\<hostInBrowser />** elemento al manifesto dell'applicazione (*\<projectname> . exe. manifest*) quando viene compilato un progetto di applicazione browser XAML (XBAP).

## <a name="task-parameters"></a>Parametri dell'attività

|Parametro|Descrizione|
|---------------|-----------------|
|`ApplicationManifest`|Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica il percorso e il nome del file manifesto dell'applicazione a cui si desidera aggiungere l'elemento `<hostInBrowser />`.|
|`HostInBrowser`|Parametro **Boolean** obbligatorio.<br /><br /> Specifica se modificare il manifesto dell'applicazione per includere l' **\<hostInBrowser />** elemento. Se **true**, **\<hostInBrowser />** viene incluso un nuovo elemento nell' **\<entryPoint />** elemento. L'inclusione di elementi è cumulativa: se un **\<hostInBrowser />** elemento esiste già, non viene rimosso o sovrascritto. Viene invece creato un **\<hostInBrowser />** elemento aggiuntivo. Se è **false**, il manifesto dell'applicazione non viene modificato.|

## <a name="remarks"></a>Commenti

 Le applicazioni XBAP vengono eseguite utilizzando la distribuzione ClickOnce, pertanto devono essere pubblicate con i manifesti di supporto della distribuzione e dell'applicazione. MSBuild utilizza l'attività [GenerateApplicationManifest](generateapplicationmanifest-task.md) per generare un manifesto dell'applicazione.

 Quindi, per configurare un'applicazione da ospitare da un browser, **\<hostInBrowser />** è necessario aggiungere un elemento aggiuntivo al manifesto dell'applicazione, come illustrato nell'esempio seguente:

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

 L' <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> attività viene eseguita quando viene compilato un progetto XBAP per aggiungere l' `<hostInBrowser />` elemento.

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

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/wpf-msbuild-task-reference.md)
- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Creazione di un'applicazione WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Panoramica delle applicazioni browser XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)