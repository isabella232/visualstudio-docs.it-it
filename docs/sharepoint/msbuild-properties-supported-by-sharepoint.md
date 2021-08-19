---
title: MSBuild Proprietà supportate da SharePoint | Microsoft Docs
description: Leggere un elenco di MSBuild di proprietà e descrizioni supportate da e sono specifiche per SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, MSBuild properties
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 66024105ac41c6c72d7eec019d507183fdd7479a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115551"
---
# <a name="msbuild-properties-supported-by-sharepoint"></a>Proprietà di MsBuild supportate da SharePoint
  Qualsiasi [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] proprietà definita nel file Microsoft.VisualStudio.SharePoint.targets, nel file di progetto o nel file utente del progetto può essere usata nei SharePoint [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] progetto. Oltre alle proprietà comuni fornite dal progetto, SharePoint definisce proprietà aggiuntive specifiche per i [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] SharePoint progetto.

 Per un elenco delle proprietà [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] comuni, vedere [Proprietà MSBuild Project comuni](/previous-versions/dotnet/netframework-4.0/bb629394(v=vs.100)). Per un elenco completo delle proprietà supportate dal linguaggio di programmazione, cercare nel file *targets,* nel file di progetto (*csproj* o *vbproj*) o nel file utente del progetto (*csproj.user* o *vbproj.user*).

## <a name="msbuild-properties-specific-to-sharepoint"></a>Proprietà di MsBuild specifiche per SharePoint
 Nella tabella seguente sono elencate le proprietà che si applicano in modo [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] specifico SharePoint progetti in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Esistono altre proprietà, ma sono per uso interno.

|Nome proprietà|Descrizione|
|-------------------|-----------------|
|SharePointSiteUrl|Stringa che rappresenta [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] l'oggetto per SharePoint sito.|
|SandboxedSolution|Valore booleano che indica se la soluzione è una soluzione in modalità sandbox.|
|ActiveDeploymentConfiguration|Configurazione della distribuzione attiva.|
|IncludeAssemblyInPackage|Valore booleano che indica se l'assembly è incluso nel file del pacchetto.|
|PreDeploymentCommand|Valore stringa che rappresenta il comando da eseguire nel passaggio del comando di pre-distribuzione.|
|PostDeploymentCommand|Valore stringa che rappresenta il comando da eseguire nel passaggio del comando post-distribuzione.|
|CustomBeforeSharePointTargets|Stringa che rappresenta il percorso di un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] file di destinazione. Se il file di destinazione esiste e viene definito, viene importato prima SharePoint dati di destinazione. Questa proprietà consente di personalizzare il processo del pacchetto definendo le proprietà correlate alla creazione di pacchetti senza modificare il file di destinazione SharePoint spedito, ma il file di destinazione si applica ancora a tutti i SharePoint progetto.|
|CustomAfterSharePointTargets|Stringa che rappresenta il percorso di un [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] file di destinazione. Se il file di destinazione esiste e viene definito, viene importato dopo tutti i dati SharePoint destinazione. Questa proprietà consente di personalizzare il processo del pacchetto eseguendo l'override delle proprietà e delle destinazioni correlate alla creazione di pacchetti senza dover modificare il file di destinazione di SharePoint spedito, ma il file di destinazione si applica ancora a tutti i SharePoint progetto.|
|LayoutPath|Stringa che rappresenta la directory radice in cui vengono inseriti temporaneamente tutti i file da inserire nel pacchetto prima di essere aggiunti al file *con estensione wsp.* Questo percorso può essere utile per sapere quando si esegue l'override delle destinazioni BeforeLayout e AfterLayout per aggiungere, rimuovere o modificare i file da creare in un pacchetto, perché è possibile usarlo per modificare il contenuto del file *con estensione wsp.*|
|BasePackagePath|Stringa che rappresenta la cartella in cui viene inserito il pacchetto. Questo valore usa la directory di output del progetto, ad esempio Bin\Debug.|
|PackageExtension|Stringa che rappresenta l'estensione di file da aggiungere al pacchetto. Il valore predefinito è wsp.|
|AssemblyDeploymentTarget|Stringa che rappresenta il percorso in cui viene distribuito l'assembly del progetto SharePoint server. Il valore è GlobalAssemblyCache (impostazione predefinita) o WebApplication. Questa proprietà può essere impostata anche nel Finestra Proprietà.|
|PackageWithValidation|Valore booleano che specifica se la convalida viene eseguita prima della creazione del pacchetto. Questa proprietà consente di ignorare gli errori di convalida durante la compilazione dei pacchetti.|
|ValidatePackageDependsOn|Stringa che definisce destinazioni aggiuntive da eseguire prima della destinazione ValidatePackage.|
|TokenReplacementFileExensions|Stringa che definisce i file che hanno i token sostituiti durante la creazione del pacchetto.|

## <a name="use-msbuild-properties-in-the-properties-page"></a>Usare le proprietà di MsBuild nella pagina delle proprietà
 Per maggiore flessibilità, anziché usare stringhe hard coded nelle caselle Riga di comando **pre-distribuzione** e Riga di comando **post-distribuzione** nella pagina Proprietà SharePoint è possibile usare le proprietà SharePoint come argomenti. Ad esempio, anziché specificare una stringa specifica per il sito SharePoint, è possibile usare [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] `$(SharePointSiteUrl)` .

> [!NOTE]
> È possibile usare la sintassi [!INCLUDE[vstecmsbuild](../sharepoint/includes/vstecmsbuild-md.md)] della variabile `$(` *propertyName* o la sintassi della variabile di ambiente `)` `%` *propertyName* `%` per specificare una proprietà.

## <a name="see-also"></a>Vedi anche

- [MSBuild Riferimento](../msbuild/msbuild-reference.md)