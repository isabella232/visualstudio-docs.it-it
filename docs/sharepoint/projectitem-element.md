---
title: Elemento ProjectItem | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 44fc1b918960f0268d916ccfa560f118cea47144
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536877"
---
# <a name="projectitem-element"></a>ProjectItem (elemento)
  Rappresenta un elemento del progetto SharePoint. Questo elemento è l'elemento radice obbligatorio del file con *estensione spdata* .

## <a name="syntax"></a>Sintassi

```xml
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"
    SupportedTrustLevels = "Trust levels that the project item supports"
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"
    Type="Identifier for the project item">
  <Files>...</Files>
  <ProjectItemFolder>...</ProjectItemFolder>
  <SafeControls>...</SafeControls>
  <FeatureProperties>...</FeatureProperties>
  <ExtensionData>...</ExtensionData>
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|**DefaultFile**|Attributo **xs: String** facoltativo.<br /><br /> Percorso relativo, incluso il nome file, del file che viene aperto nell'editor di Visual Studio quando si apre l'elemento del progetto SharePoint in **Esplora soluzioni**. Il percorso è relativo rispetto alla cartella che contiene il file con *estensione spdata* .|
|**FeatureReceiverClass**|Attributo **xs: String** facoltativo.<br /><br /> Nome completo di una classe del ricevitore di funzionalità per questo elemento del progetto SharePoint. Per ulteriori informazioni sui ricevitori di funzionalità, vedere la pagina relativa [alla creazione di pacchetti e informazioni sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|
|**FeatureReceiverAssembly**|Attributo **xs: String** facoltativo.<br /><br /> Specifica il nome completo di un assembly che definisce un ricevitore di funzionalità per questo elemento del progetto SharePoint. Per ulteriori informazioni sui ricevitori di funzionalità, vedere la pagina relativa [alla creazione di pacchetti e informazioni sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Per ulteriori informazioni sui nomi di assembly completi, vedere [nomi degli assembly](/dotnet/framework/app-domains/assembly-names).|
|**SupportedTrustLevels**|Attributo **xs: String** facoltativo.<br /><br /> Specifica i livelli di attendibilità supportati da questo elemento del progetto SharePoint. Il valore può essere una delle seguenti stringhe: sandboxed, FullTrust o all. Il valore all specifica sia sandboxed che FullTrust.<br /><br /> In un tipo di elemento di progetto SharePoint personalizzato, il valore di questo attributo corrisponde al valore assegnato alla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> proprietà nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo. Se si specifica un valore diverso per questo attributo, Visual Studio sovrascrive il valore in modo che specifichi lo stesso livello di attendibilità specificato nella <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> Proprietà.|
|**SupportedDeploymentScopes**|Attributo **xs: String** facoltativo.<br /><br /> Specifica gli ambiti di distribuzione supportati da questo elemento del progetto SharePoint. Questo valore è una stringa delimitata da virgole costituita da una o più delle seguenti stringhe: Farm, sito, Web, applicazione Web o pacchetto. Ad esempio: `Web, Site`<br /><br /> In un tipo di elemento di progetto SharePoint personalizzato, il valore di questo attributo corrisponde al valore assegnato alla <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> proprietà nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo. Se si specifica un valore diverso per questo attributo, Visual Studio sovrascrive il valore in modo che specifichi lo stesso livello di attendibilità specificato nella <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> Proprietà.|
|**Tipo**|Attributo **xs: String** obbligatorio.<br /><br /> Identificatore per l'elemento del progetto SharePoint. In un tipo di elemento di progetto SharePoint personalizzato, l'identificatore è la stringa passata a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Per altre informazioni, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Per un elenco degli identificatori per gli elementi del progetto SharePoint incorporati inclusi in Visual Studio, vedere [estendere gli elementi del progetto SharePoint](../sharepoint/extending-sharepoint-project-items.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di elementi di dati personalizzati associati all'elemento del progetto SharePoint.<br /><br /> È possibile includere un solo elemento **ExtensionData** .|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di valori di proprietà inclusi in una funzionalità quando viene distribuita in SharePoint.<br /><br /> È possibile includere un solo elemento **FeatureProperties** .|
|[File](../sharepoint/files-element.md)|Elemento **FileCollectionType** facoltativo.<br /><br /> Specifica i file da distribuire con l'elemento del progetto SharePoint, ad esempio i file degli elementi delle funzionalità e l'output dei progetti non SharePoint dipendenti.<br /><br /> Includere un elemento **file** o **ProjectItemFolder** , ma non entrambi.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Elemento **ProjectItemFolderType** facoltativo.<br /><br /> Rappresenta una cartella mappata.<br /><br /> Includere un elemento **file** o **ProjectItemFolder** , ma non entrambi.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di controlli ASPX e Web part designati come sicuri per qualsiasi utente per accedere a qualsiasi pagina ASPX nel sito di SharePoint.<br /><br /> È possibile includere un solo elemento **SafeControls** .|

### <a name="parent-elements"></a>Elementi padre
 No.

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.Microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|Schema dell'elemento del progetto SharePoint|
|**File di convalida**|ProjectItemModelSchema. xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
[Schema dell'elemento del progetto SharePoint rseference](../sharepoint/sharepoint-project-item-schema-reference.md)
