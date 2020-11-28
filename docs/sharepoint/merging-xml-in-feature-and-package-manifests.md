---
title: Unione di codice XML in manifesti di funzionalità e pacchetti | Microsoft Docs
description: Codice XML generato dalla finestra di progettazione di merge e codice XML aggiunto dall'utente nei manifesti di funzionalità e pacchetto di SharePoint. Informazioni sugli elementi del manifesto della funzionalità e del pacchetto e sulle eccezioni di Unione.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 16305ed63f48d9f14e35aeb8d37e35f23f40be25
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304228"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Unisci XML in manifesti di funzionalità e pacchetto
  Le funzionalità e i pacchetti sono definiti da [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] file manifesto. Questi manifesti in pacchetto sono una combinazione di dati generati dalle finestre di progettazione e personalizzati [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] immessi nel modello di manifesto dagli utenti. Al momento della creazione del [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacchetto, unisce le [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] istruzioni personalizzate con la finestra di progettazione fornita [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] per formare il [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] file manifesto del pacchetto. Gli elementi simili, con le eccezioni annotate più avanti in eccezioni di merge, vengono uniti per evitare [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] errori di convalida dopo la distribuzione dei file in SharePoint e per rendere i file manifesto più piccoli ed efficienti.

## <a name="modify-the-manifests"></a>Modificare i manifesti
 Non è possibile modificare direttamente i file manifesto del pacchetto fino a quando non si disabilita la funzionalità o i progettisti di pacchetti. Tuttavia, è possibile aggiungere manualmente [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementi personalizzati al modello di manifesto tramite le finestre di progettazione di funzionalità e di pacchetti o l' [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Editor. Per ulteriori informazioni, vedere [procedura: personalizzare una funzionalità di SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) e [procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).

## <a name="feature-and-package-manifest-merge-process"></a>Processo di merge del manifesto della funzionalità e del pacchetto
 Quando si combinano elementi personalizzati insieme agli elementi forniti dalla finestra di progettazione, in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] viene utilizzato il processo seguente. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Verifica se ogni elemento ha un valore di chiave univoco. Se un elemento non dispone di valori di chiave univoci, viene aggiunto al file manifesto inserito nel pacchetto. Analogamente, gli elementi che dispongono di più chiavi non possono essere sottoposti a merge. Vengono pertanto aggiunti al file manifesto.

 Se un elemento ha una chiave univoca, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Confronta i valori della finestra di progettazione e delle chiavi personalizzate. Se i valori corrispondono, vengono uniti in un singolo valore. Se i valori sono diversi, il valore della chiave della finestra di progettazione viene ignorato e viene utilizzato il valore della chiave personalizzata. Anche le raccolte sono unite. Se, ad esempio, l'oggetto generato dalla finestra di progettazione [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] e l'oggetto personalizzato [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] contengono entrambi una raccolta di assembly, il manifesto del pacchetto contiene solo una raccolta di assembly.

## <a name="merge-exceptions"></a>Eccezioni di merge
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unisce la maggior parte [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] degli elementi della finestra di progettazione con elementi personalizzati simili, purché [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] dispongano di un unico attributo di identificazione univoco. Tuttavia, alcuni elementi non dispongono dell'identificatore univoco necessario per l' [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Unione. Questi elementi sono noti come *eccezioni di Unione*. In questi casi, non [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unisce gli elementi personalizzati [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] insieme agli elementi forniti dalla finestra [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] di progettazione, ma li aggiunge al file manifesto del pacchetto.

 Di seguito è riportato un elenco di eccezioni di merge per i file manifesto delle funzionalità e dei pacchetti [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] .

|Designer|Elemento XML|
|--------------|-----------------|
|Progettazione funzionalità|ActivationDependency|
|Progettazione funzionalità|UpgradeAction|
|Progettazione pacchetti|SafeControl|
|Progettazione pacchetti|CodeAccessSecurity|

## <a name="feature-manifest-elements"></a>Elementi del manifesto della funzionalità
 La tabella seguente è un elenco di tutti gli elementi manifesto della funzionalità che possono essere Uniti e della relativa chiave univoca usata per la corrispondenza.

|Nome dell'elemento|Chiave univoca|
|------------------|----------------|
|Funzionalità (tutti gli attributi)|*Nome attributo* (ogni nome di attributo dell'elemento Feature è una chiave univoca).|
|ElementFile|Location|
|ElementManifests/ElementManifest|Location|
|Proprietà/Proprietà|Chiave|
|CustomUpgradeAction|Nome|
|CustomUpgradeActionParameter|Nome|

> [!NOTE]
> Poiché l'unico modo per modificare l'elemento CustomUpgradeAction è nell'editor personalizzato [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] , l'effetto della mancata unione è basso.

## <a name="package-manifest-elements"></a>Elementi manifesto del pacchetto
 La tabella seguente è un elenco di tutti gli elementi del manifesto del pacchetto che possono essere Uniti e della relativa chiave univoca usata per la corrispondenza.

|Nome dell'elemento|Chiave univoca|
|------------------|----------------|
|Soluzione (tutti gli attributi)|*Nome attributo* (ogni nome di attributo dell'elemento della soluzione è una chiave univoca).|
|ApplicationResourceFiles/Elemento ApplicationResourceFile|Location|
|Assembly/assembly|Location|
|ClassResources/ClassResource|Location|
|DwpFiles/DwpFile|Location|
|FeatureManifests/FeatureManifest|Location|
|Risorse/risorsa|Location|
|RootFiles/RootFile|Location|
|SiteDefinitionManifests/SiteDefinitionManifest|Location|
|WebTempFile|Location|
|TemplateFiles della/TemplateFile|Location|
|SolutionDependency|SolutionID|

## <a name="manually-add-deployed-files"></a>Aggiungere manualmente i file distribuiti
 Alcuni elementi del manifesto, ad esempio Elemento ApplicationResourceFile e DwpFiles, specificano un percorso che include un nome file. Tuttavia, se si aggiunge una voce di nome file al modello di manifesto, il file sottostante non viene aggiunto al pacchetto. È necessario aggiungere il file al progetto per includerlo nel pacchetto e impostare la relativa proprietà del tipo di distribuzione di conseguenza.

## <a name="see-also"></a>Vedere anche
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
- [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
