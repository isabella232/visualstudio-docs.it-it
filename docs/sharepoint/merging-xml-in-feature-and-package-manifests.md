---
title: Unione di xml in manifesti di funzionalità e | Microsoft Docs
description: Unire codice XML generato dalla finestra di progettazione e aggiunto dall'utente SharePoint manifesti di funzionalità e pacchetti. Informazioni su elementi del manifesto di funzionalità e pacchetti ed eccezioni di unione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: c4af8e25fa998804e56359faa29cd7e5651336218003100f60fac379fcc5f641
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121244316"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Unire XML nei manifesti di funzionalità e pacchetti
  Le funzionalità e i pacchetti sono definiti dai [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] file manifesto. Questi manifesti in pacchetto sono una combinazione di dati generati dalle finestre di progettazione e personalizzati immessi nel [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] modello di manifesto dagli utenti. In fase di creazione del pacchetto, unisce le istruzioni personalizzate con la finestra di progettazione fornita [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] per [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] formare il file manifesto in [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pacchetto. Elementi simili, con le eccezioni notate più avanti in Merge Exceptions (Eccezioni di unione), vengono uniti per evitare errori di convalida dopo la distribuzione dei file in SharePoint e per rendere i file manifesto più piccoli ed [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] efficienti.

## <a name="modify-the-manifests"></a>Modificare i manifesti
 Non è possibile modificare direttamente i file manifesto in pacchetto fino a quando non si disabilitano le finestre di progettazione della funzionalità o del pacchetto. Tuttavia, è possibile aggiungere manualmente elementi personalizzati al modello di manifesto tramite le finestre di progettazione di funzionalità e [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pacchetti o [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] l'editor. Per altre informazioni, vedere [Procedura: Personalizzare una funzionalità SharePoint e](../sharepoint/how-to-customize-a-sharepoint-feature.md) [Procedura: Personalizzare un pacchetto SharePoint soluzione.](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)

## <a name="feature-and-package-manifest-merge-process"></a>Processo di unione di manifesti di funzionalità e pacchetti
 Quando si combinano elementi personalizzati con elementi forniti dalla finestra di progettazione, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] usa il processo seguente. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] controlla se ogni elemento ha un valore di chiave univoca. Se un elemento non dispone di valori di chiave univoci, viene aggiunto al file manifesto inserito nel pacchetto. Analogamente, gli elementi che dispongono di più chiavi non possono essere sottoposti a merge. Di conseguenza, vengono aggiunti al file manifesto.

 Se un elemento ha una chiave univoca, confronta i valori della finestra di progettazione e [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] le chiavi personalizzate. Se i valori corrispondono, vengono uniti in un singolo valore. Se i valori sono diversi, il valore della chiave della finestra di progettazione viene ignorato e viene utilizzato il valore della chiave personalizzata. Vengono unite anche le raccolte. Ad esempio, se il file generato dalla finestra di progettazione e l'oggetto personalizzato contengono entrambi una raccolta Assemblies, il manifesto in pacchetto contiene una [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] sola raccolta Assemblies.

## <a name="merge-exceptions"></a>Unire le eccezioni
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unisce la maggior parte degli elementi della finestra di progettazione [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] con [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementi personalizzati simili, purché presentino un singolo attributo di identificazione univoco. Tuttavia, alcuni elementi non dispongono dell'identificatore univoco necessario per [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] l'unione. Questi elementi sono noti come *eccezioni di unione.* In questi casi, non unisce gli elementi personalizzati con gli elementi forniti dalla finestra di progettazione, ma li aggiunge [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] al file manifesto in [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] pacchetto.

 Di seguito è riportato un elenco di eccezioni di unione per i file manifesto di funzionalità [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] e pacchetti.

|Designer|Elemento XML|
|--------------|-----------------|
|Progettazione funzionalità|ActivationDependency|
|Progettazione funzionalità|UpgradeAction|
|Progettazione pacchetti|SafeControl|
|Progettazione pacchetti|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>Elementi del manifesto della funzionalità
 La tabella seguente contiene un elenco di tutti gli elementi del manifesto delle funzionalità che è possibile unire e la relativa chiave univoca usata per la corrispondenza.

|Nome dell'elemento|Chiave univoca|
|------------------|----------------|
|Funzionalità (tutti gli attributi)|*Nome attributo* (ogni nome di attributo dell'elemento Feature è una chiave univoca).|
|ElementFile|Località|
|ElementManifests/ElementManifest|Località|
|Proprietà/Proprietà|Chiave|
|CustomUpgradeAction|Nome|
|CustomUpgradeActionParameter|Nome|

> [!NOTE]
> Poiché l'unico modo per modificare l'elemento CustomUpgradeAction è nell'editor personalizzato, l'effetto della non unione [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] è basso.

## <a name="package-manifest-elements"></a>Elementi del manifesto del pacchetto
 Nella tabella seguente è riportato un elenco di tutti gli elementi manifesto del pacchetto che è possibile unire e la relativa chiave univoca utilizzata per la corrispondenza.

|Nome dell'elemento|Chiave univoca|
|------------------|----------------|
|Soluzione (tutti gli attributi)|*Nome attributo* (ogni nome di attributo dell'elemento Solution è una chiave univoca).|
|ApplicationResourceFiles/ApplicationResourceFile|Località|
|Assembly/Assembly|Località|
|ClassResources/ClassResource|Località|
|DwpFiles/DwpFile|Località|
|FeatureManifests/FeatureManifest|Località|
|Risorse/Risorsa|Località|
|RootFiles/RootFile|Località|
|SiteDefinitionManifests/SiteDefinitionManifest|Località|
|WebTempFile|Località|
|TemplateFiles/TemplateFile|Località|
|Dipendenza della soluzione|ID soluzione|

## <a name="manually-add-deployed-files"></a>Aggiungere manualmente i file distribuiti
 Alcuni elementi manifesto, ad esempio ApplicationResourceFile e DwpFiles, specificano un percorso che include un nome file. Tuttavia, l'aggiunta di una voce di nome file al modello di manifesto non aggiunge il file sottostante al pacchetto. È necessario aggiungere il file al progetto per includerlo nel pacchetto e impostarne la proprietà Tipo di distribuzione di conseguenza.

## <a name="see-also"></a>Vedi anche
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
