---
title: Proprietà MSBuild supportate in SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 55561d570605cfd5690fc0459444b2fbadeca51a
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684808"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Proprietà MsBuild supportate in SharePoint
  Eventuali [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] proprietà definita nel file targets, file di progetto o file di progetto utente sono utilizzabili in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetti SharePoint. Oltre alla comune [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] proprietà fornita dal progetto di SharePoint definisce proprietà aggiuntive specifiche per i progetti SharePoint.  
  
 Per un elenco di common [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] proprietà, vedere [proprietà di progetto MSBuild comuni](http://go.microsoft.com/fwlink/?LinkID=168687). Per un elenco completo delle proprietà supportate dal linguaggio di programmazione, esaminare il *targets* file, il file di progetto (*csproj* oppure *vbproj*), o l'utente di progetto di file ( *vbproj* oppure *. vbproj*).  
  
## <a name="msbuild-properties-specific-to-sharepoint"></a>Proprietà di MsBuild specifiche di SharePoint
 La tabella seguente elenca [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] delle proprietà si applicano specificatamente ai progetti SharePoint nella [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Sono presenti altre proprietà, ma sono per uso interno.  
  
|Nome proprietà|Descrizione|  
|-------------------|-----------------|  
|SharePointSiteUrl|Stringa che rappresenta il [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] al sito di SharePoint.|  
|SandboxedSolution|Valore booleano che indica se la soluzione è una soluzione creata mediante sandbox.|  
|ActiveDeploymentConfiguration|La configurazione distribuzione attiva.|  
|IncludeAssemblyInPackage|Valore booleano che indica se l'assembly viene incluso nel file del pacchetto.|  
|PreDeploymentCommand|Valore stringa che rappresenta il comando da eseguire nel passaggio comando pre-distribuzione.|  
|PostDeploymentCommand|Valore stringa che rappresenta il comando da eseguire nel passaggio comando post-distribuzione.|  
|CustomBeforeSharePointTargets|Stringa che rappresenta il percorso di un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] file di destinazioni. Se il file di destinazioni esiste ed è definito, l'importazione prima di qualsiasi dato di destinazioni di SharePoint. Questa proprietà consente di personalizzare il processo del pacchetto dalle proprietà correlate alla creazione di pacchetti predefinendo senza modificare il file targets incluso in SharePoint, anche se il file di destinazioni ancora si applica a tutti i progetti SharePoint.|  
|CustomAfterSharePointTargets|Stringa che rappresenta il percorso di un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] file di destinazioni. Se il file di destinazioni esiste ed è definito, è Dopotutto importato le destinazioni dati di SharePoint. Questa proprietà consente di personalizzare il processo del pacchetto eseguendo l'override di proprietà correlate alla creazione di pacchetti e le destinazioni senza dover modificare il file targets incluso in SharePoint, anche se il file di destinazioni ancora si applica a tutti i progetti SharePoint.|  
|LayoutPath|Stringa che rappresenta la directory radice in cui ognuno dei file da includere nel pacchetto sono temporaneamente inseriti prima di essere aggiunti al *wsp* file. Questo percorso può essere utile conoscere quando si esegue l'override di destinazioni di BeforeLayout e AfterLayout per aggiungere, rimuovere o modificare i file devono essere preparati, quanto è possibile utilizzarlo per modificare il contenuto del *wsp* file.|  
|BasePackagePath|Stringa che rappresenta la cartella in cui viene inserito il pacchetto. Questo valore viene utilizzata la directory di output del progetto, ad esempio Bin\Debug.|  
|PackageExtension|Stringa che rappresenta l'estensione del nome file da aggiungere al pacchetto. Il valore predefinito è wsp.|  
|AssemblyDeploymentTarget|Stringa che rappresenta la posizione in cui l'assembly del progetto viene distribuito nel server SharePoint. Il valore è GlobalAssemblyCache (predefinito) o WebApplication. Questa proprietà può anche essere impostata nella finestra Proprietà.|  
|PackageWithValidation|Valore booleano che specifica se la convalida viene eseguita prima della creazione del pacchetto. Questa proprietà consente di ignorare gli errori di convalida durante la compilazione di pacchetti.|  
|ValidatePackageDependsOn|Stringa che definisce le destinazioni aggiuntive da eseguire prima della destinazione ValidatePackage.|  
|TokenReplacementFileExensions|Stringa che definisce i file con i relativi token sostituiti durante la creazione di pacchetti.|  
  
## <a name="use-msbuild-properties-in-the-properties-page"></a>Usare le proprietà di MsBuild nella pagina delle proprietà
 Per una flessibilità, invece di usare le stringhe hardcoded nel **riga di comando di pre-distribuzione** e **riga di comando di post-distribuzione** caselle nella pagina delle proprietà di SharePoint, è possibile utilizzare SharePoint proprietà come argomenti. Ad esempio, anziché specificare una determinata [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] stringa per il sito di SharePoint, è possibile usare `$(SharePointSiteUrl)`.  
  
> [!NOTE]  
>  È possibile usare la [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] variabile sintassi `$(` *propertyName* `)` o la sintassi della variabile di ambiente `%` *propertyName* `%` Per specificare una proprietà.  
  
## <a name="see-also"></a>Vedere anche

- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)  