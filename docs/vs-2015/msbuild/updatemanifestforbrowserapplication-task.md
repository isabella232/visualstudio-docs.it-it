---
title: Attività UpdateManifestForBrowserApplication | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dffa98a8abbf74bd6eee8761d91f09a7c022666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68740224"
---
# <a name="updatemanifestforbrowserapplication-task"></a>Attività UpdateManifestForBrowserApplication
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L' <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> attività viene eseguita per aggiungere l' **\<hostInBrowser />** elemento al manifesto dell'applicazione (*NomeProgetto*. exe. manifest) quando [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] viene compilato un progetto.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`ApplicationManifest`|Parametro **ITaskItem[]** obbligatorio.<br /><br /> Specifica il percorso e il nome del file manifesto dell'applicazione a cui si desidera aggiungere l'elemento `<hostInBrowser />`.|  
|`HostInBrowser`|Parametro **Boolean** obbligatorio.<br /><br /> Specifica se modificare il manifesto dell'applicazione per includere l' **\<hostInBrowser />** elemento. Se **true**, `<` viene incluso un nuovo elemento **HostInBrowser/>** nell' **\<entryPoint />** elemento. Si noti che l'inclusione di elementi è cumulativa: se un **\<hostInBrowser />** elemento esiste già, non viene rimosso o sovrascritto. Viene invece creato un **\<hostInBrowser />** elemento aggiuntivo. Se **false**, il manifesto dell'applicazione non viene modificato.|  
  
## <a name="remarks"></a>Osservazioni  
 [!INCLUDE[TLA2#tla_xbap#plural](../includes/tla2sharptla-xbapsharpplural-md.md)] vengono eseguiti tramite la distribuzione di [!INCLUDE[TLA#tla_clickonce](../includes/tlasharptla-clickonce-md.md)] e pertanto devono essere pubblicati con manifesti di supporto dell'applicazione e della distribuzione. [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] usa l'attività [GenerateApplicationManifest](/dotnet/api/microsoft.build.tasks.generateapplicationmanifest) per generare un manifesto dell'applicazione.  
  
 Quindi, per configurare un'applicazione da ospitare da un browser, **\<hostInBrowser />** è necessario aggiungere un elemento aggiuntivo al manifesto dell'applicazione, come illustrato nell'esempio seguente:  
  
```  
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
  
 L'attività <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> viene eseguita quando viene compilato un progetto [!INCLUDE[TLA2#tla_xbap](../includes/tla2sharptla-xbap-md.md)] per aggiungere l'elemento `<hostInBrowser />`.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato come verificare che l'elemento `<hostInBrowser />` sia incluso in un file manifesto dell'applicazione.  
  
```  
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
 [Riferimenti a MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Riferimento attività](../msbuild/wpf-msbuild-task-reference.md)   
 [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimento attività](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Panoramica delle applicazioni browser XAML di WPF](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
