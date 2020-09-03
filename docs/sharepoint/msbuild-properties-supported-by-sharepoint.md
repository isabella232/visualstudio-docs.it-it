---
title: Proprietà di MSBuild supportate da SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5470160c6b0af1af39238a14319ad497e1541a43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985169"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Proprietà di MsBuild supportate da SharePoint
  Qualsiasi [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] proprietà definita nel file Microsoft. VisualStudio. SharePoint. targets, nel file di progetto o nel file utente del progetto può essere utilizzata nei [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetti SharePoint. Oltre alle [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Proprietà comuni fornite dal progetto, SharePoint definisce proprietà aggiuntive specifiche dei progetti SharePoint.

 Per un elenco delle [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] Proprietà comuni, vedere [Proprietà comuni del progetto MSBuild](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100)). Per un elenco completo delle proprietà supportate dal linguaggio di programmazione, esaminare il file con *estensione targets* , il file di progetto (con*estensione csproj* o *VBPROJ*) o il file utente del progetto (*csproj. User* o *. vbproj. User*).

## <a name="msbuild-properties-specific-to-sharepoint"></a>Proprietà di MsBuild specifiche di SharePoint
 Nella tabella seguente sono elencate le [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] proprietà che si applicano in modo specifico ai progetti SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Esistono altre proprietà, ma sono per uso interno.

|Nome proprietà|Descrizione|
|-------------------|-----------------|
|SharePointSiteUrl|Stringa che rappresenta il [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] al sito di SharePoint.|
|SandboxedSolution|Valore booleano che indica se la soluzione è una soluzione in modalità sandbox.|
|ActiveDeploymentConfiguration|Configurazione della distribuzione attiva.|
|IncludeAssemblyInPackage|Valore booleano che indica se l'assembly è incluso nel file del pacchetto.|
|PreDeploymentCommand|Valore stringa che rappresenta il comando da eseguire nel passaggio del comando pre-distribuzione.|
|PostDeploymentCommand|Valore stringa che rappresenta il comando da eseguire nel passaggio del comando post-distribuzione.|
|CustomBeforeSharePointTargets|Stringa che rappresenta il percorso di un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] file di destinazioni. Se il file di destinazioni esiste e viene definito, viene importato prima di qualsiasi destinazione di SharePoint. Questa proprietà consente di personalizzare il processo del pacchetto predefinendo le proprietà correlate al packaging senza modificare il file di destinazioni di SharePoint spedito, ma il file di destinazioni si applica comunque a tutti i progetti SharePoint.|
|CustomAfterSharePointTargets|Stringa che rappresenta il percorso di un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] file di destinazioni. Se il file di destinazioni esiste e viene definito, viene importato dopo tutti i dati di destinazione di SharePoint. Questa proprietà consente di personalizzare il processo del pacchetto eseguendo l'override delle destinazioni e delle proprietà correlate al packaging senza dover modificare il file di destinazioni di SharePoint spedito, ma il file di destinazioni si applica comunque a tutti i progetti SharePoint.|
|LayoutPath|Stringa che rappresenta la directory radice in cui ogni file da inserire nel pacchetto viene temporaneamente inserito prima di essere aggiunto al file con *estensione wsp* . Questo percorso può essere utile quando si esegue l'override delle destinazioni BeforeLayout e AfterLayout per aggiungere, rimuovere o modificare i file da inserire nel pacchetto, perché è possibile usarlo per modificare il contenuto del file con estensione *WSP* .|
|BasePackagePath|Stringa che rappresenta la cartella in cui si trova il pacchetto. Questo valore usa la directory di output del progetto, ad esempio Bin\Debug.|
|PackageExtension|Stringa che rappresenta l'estensione del nome file da accodare al pacchetto. Il valore predefinito è WSP.|
|AssemblyDeploymentTarget|Stringa che rappresenta la posizione in cui l'assembly del progetto viene distribuito nel server SharePoint. Il valore è GlobalAssemblyCache (impostazione predefinita) o WebApplication. Questa proprietà può essere impostata anche nella Finestra Proprietà.|
|PackageWithValidation|Valore booleano che specifica se la convalida viene eseguita prima della creazione del pacchetto. Questa proprietà consente di ignorare gli errori di convalida durante la compilazione dei pacchetti.|
|ValidatePackageDependsOn|Stringa che definisce destinazioni aggiuntive da eseguire prima della destinazione ValidatePackage.|
|TokenReplacementFileExensions|Stringa che definisce i file per i quali i token vengono sostituiti durante la creazione del pacchetto.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>Usare le proprietà di MsBuild nella pagina proprietà
 Per flessibilità, anziché usare stringhe hardcoded nelle caselle della riga di comando di **pre-distribuzione** e della **riga di comando post-distribuzione** nella pagina delle proprietà di SharePoint, è possibile usare le proprietà di SharePoint come argomenti. Anziché specificare una [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] stringa specifica per il sito di SharePoint, ad esempio, è possibile utilizzare `$(SharePointSiteUrl)` .

> [!NOTE]
> È possibile utilizzare la [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] sintassi della variabile `$(` *PropertyName* `)` o la sintassi della variabile `%` di ambiente *PropertyName* `%` per specificare una proprietà.

## <a name="see-also"></a>Vedere anche

- [Riferimenti a MSBuild](../msbuild/msbuild-reference.md)