---
title: Unione di codice XML delle funzionalità e pacchetto manifesti | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 30c339bf38f8fc873b27b9c213fad21d66fb9fa7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914436"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Unire i dati XML nei manifesti di funzionalità e pacchetto
  Le funzionalità e i pacchetti sono definiti da [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] file manifesto. Questi manifesti di pacchetto sono una combinazione dei dati generati da finestre di progettazione e custom [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] immesso nel modello di manifesto da parte degli utenti. In fase di creazione dei pacchetti [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] unisce l'oggetto personalizzato [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] istruzioni con la finestra di progettazione fornito dal [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] in modo da formare il pacchetto [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] file manifesto. Gli elementi simili, con le eccezioni riportate più avanti in eccezioni di tipo Merge, vengono uniti per evitare [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] gli errori di convalida dopo aver distribuito i file in SharePoint e per rendere il manifesto i file più piccoli e più efficiente.  
  
## <a name="modify-the-manifests"></a>Modificare i manifesti
 Fino a quando non si disabilita le finestre di progettazione di funzionalità o un pacchetto, è possibile modificare direttamente i file manifesto nel pacchetto. Tuttavia, è possibile aggiungere manualmente custom [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementi al modello di manifesto tramite le finestre di progettazione di funzionalità e pacchetto o [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editor. Per altre informazioni, vedere [Procedura: Personalizzare una funzionalità di SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md) e [come: Personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## <a name="feature-and-package-manifest-merge-process"></a>Funzionalità e pacchetti del manifesto del processo di merge
 Quando si combinano gli elementi personalizzati insieme a elements fornita da progettazione, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] procede come segue. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verifica se ogni elemento ha un valore di chiave univoco. Se un elemento non dispone di valori di chiave univoci, viene aggiunto al file manifesto inserito nel pacchetto. Analogamente, gli elementi che dispongono di più chiavi non possono essere sottoposti a merge. Di conseguenza, questi vengono aggiunti al file manifesto.  
  
 Se un elemento contiene una chiave univoca, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] confronta i valori della finestra di progettazione e i codici personalizzati. Se i valori corrispondono, queste vengono unite in un singolo valore. Se i valori sono diversi, il valore della chiave della finestra di progettazione viene eliminato e viene usato il valore della chiave personalizzato. Le raccolte vengono unite anche. Ad esempio, se la finestra di progettazione generati [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] e l'oggetto personalizzato [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] entrambi contengono una raccolta di assembly, il manifesto nel pacchetto contiene solo una raccolta di assembly.  
  
## <a name="merge-exceptions"></a>Le eccezioni di tipo merge
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Unisce la maggior parte delle finestra di progettazione [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementi insieme personalizzato simile [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementi fino a quando dispongono di un singolo attributo di identificazione univoco. Tuttavia, alcuni elementi non includono l'identificatore univoco richiesto per [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] unione. Questi elementi sono dette *eccezioni di tipo merge*. In questi casi [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] non supporta l'unione personalizzata [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementi insieme a progettazione fornito dal [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] elementi, ma li aggiunge al file manifesto nel pacchetto.  
  
 Seguito è riportato un elenco delle eccezioni di tipo merge per funzionalità e pacchetto [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] file manifesto.  
  
|Designer|Elemento XML|  
|--------------|-----------------|  
|Finestra di progettazione di funzionalità|ActivationDependency|  
|Finestra di progettazione di funzionalità|UpgradeAction|  
|Finestra di progettazione pacchetti|SafeControl|  
|Finestra di progettazione pacchetti|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>Elementi del manifesto funzionalità
 Nella tabella seguente è un elenco di tutti gli elementi del manifesto di funzionalità che possono essere uniti e la relativa chiave univoca che viene usato per la corrispondenza.  
  
|Nome elemento|Chiave univoca|  
|------------------|----------------|  
|Funzionalità (tutti gli attributi)|*Nome attributo* (ogni nome di attributo dell'elemento Feature è una chiave univoca).|  
|ElementFile|Percorso|  
|ElementManifests/ElementManifest|Percorso|  
|Proprietà/proprietà|Chiave|  
|CustomUpgradeAction|nome|  
|CustomUpgradeActionParameter|nome|  
  
> [!NOTE]  
>  Poiché è l'unico modo per modificare l'elemento CustomUpgradeAction personalizzato [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] editor, l'effetto di unione non è bassa.  
  
## <a name="package-manifest-elements"></a>Elementi del manifesto del pacchetto
 Nella tabella seguente è un elenco di tutti gli elementi del manifesto del pacchetto che possono essere uniti e la relativa chiave univoca che viene usato per la corrispondenza.  
  
|Nome elemento|Chiave univoca|  
|------------------|----------------|  
|Soluzione (tutti gli attributi)|*Nome attributo* (ogni nome di attributo dell'elemento Solution è una chiave univoca).|  
|Elemento ApplicationResourceFiles/ApplicationResourceFile|Percorso|  
|Assembly/Assembly|Percorso|  
|ClassResources/ClassResource|Percorso|  
|DwpFiles/DwpFile|Percorso|  
|FeatureManifests/FeatureManifest|Percorso|  
|Risorse o|Percorso|  
|RootFiles/RootFile|Percorso|  
|SiteDefinitionManifests/SiteDefinitionManifest|Percorso|  
|WebTempFile|Percorso|  
|TemplateFiles/TemplateFile|Percorso|  
|SolutionDependency|SolutionID|  
  
## <a name="manually-add-deployed-files"></a>Aggiungere manualmente i file distribuiti
 Alcuni elementi del manifesto, ad esempio ApplicationResourceFile e DwpFiles, specificano un percorso che include un nome di file. Tuttavia, aggiungendo una voce di nome file al modello di manifesto non aggiungere il file sottostante al pacchetto. È necessario aggiungere il file al progetto per includerlo nel pacchetto e impostarne la proprietà del tipo di distribuzione di conseguenza.  
  
## <a name="see-also"></a>Vedere anche
 [Il pacchetto e distribuire soluzioni di SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Build e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
