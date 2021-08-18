---
title: Elemento ProjectItem | Microsoft Docs
description: Ottenere informazioni di riferimento sull'elemento ProjectItem, che rappresenta SharePoint elemento di progetto nel SharePoint xml schema dell'elemento di progetto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: e755df78078e4fc601cd4a596813d6acd71eb781
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084194"
---
# <a name="projectitem-element"></a>ProjectItem (elemento)
  Rappresenta un SharePoint di progetto. Questo elemento è l'elemento radice obbligatorio del file *con estensione spdata.*

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
|**DefaultFile**|Facoltativo **xs: attributo** stringa.<br /><br /> Percorso relativo, incluso il nome file, del file che viene aperto nell'editor Visual Studio quando si apre l'elemento SharePoint progetto in **Esplora soluzioni**. Il percorso è relativo dalla cartella che contiene il file *con estensione spdata.*|
|**Classe FeatureReceiver**|Attributo **xs:string facoltativo.**<br /><br /> Nome completo di una classe del ricevitore di funzionalità per questo SharePoint progetto. Per altre informazioni sui ricevitori di funzionalità, vedere [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi del progetto.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)|
|**FeatureReceiverAssembly**|Attributo **xs:string facoltativo.**<br /><br /> Specifica il nome completo di un assembly che definisce un ricevitore di funzionalità per questo SharePoint progetto. Per altre informazioni sui ricevitori di funzionalità, vedere [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi del progetto.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) Per altre informazioni sui nomi di assembly completi, vedere [Nomi di assembly.](/dotnet/framework/app-domains/assembly-names)|
|**SupportedTrustLevels**|Attributo **xs:string facoltativo.**<br /><br /> Specifica i livelli di attendibilità supportati SharePoint elemento di progetto. Questo valore può essere una delle stringhe seguenti: Sandboxed, FullTrust o All. Il valore All specifica sia Sandboxed che FullTrust.<br /><br /> In un tipo SharePoint di elemento di progetto personalizzato, il valore di questo attributo corrisponde al valore assegnato alla proprietà nell'implementazione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo . Se si specifica un valore diverso per questo attributo, Visual Studio sovrascrive il valore in modo che specifichi lo stesso livello di attendibilità specificato nella <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> proprietà .|
|**SupportedDeploymentScopes**|Attributo **xs:string facoltativo.**<br /><br /> Specifica gli ambiti di distribuzione supportati da questo SharePoint progetto. Questo valore è una stringa delimitata da virgole costituita da una o più delle stringhe seguenti: Farm, Site, Web, WebApplication o Package. ad esempio `Web, Site`<br /><br /> In un tipo SharePoint di elemento di progetto personalizzato, il valore di questo attributo corrisponde al valore assegnato alla proprietà nell'implementazione <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> metodo . Se si specifica un valore diverso per questo attributo, Visual Studio sovrascrive il valore in modo che specifichi lo stesso livello di attendibilità specificato nella <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> proprietà .|
|**Tipo**|Attributo **xs:string** obbligatorio.<br /><br /> Identificatore dell'elemento SharePoint progetto. In un tipo SharePoint tipo di elemento di progetto personalizzato, l'identificatore è la stringa passata a <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Per altre informazioni, vedere [Procedura: Definire un tipo SharePoint di elemento di progetto](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Per un elenco degli identificatori per gli elementi di SharePoint predefiniti inclusi in Visual Studio, vedere Estendere SharePoint [di progetto.](../sharepoint/extending-sharepoint-project-items.md)|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di elementi di dati personalizzati associati all'SharePoint di progetto.<br /><br /> È possibile includere un solo **elemento ExtensionData.**|
|[Proprietà funzionalità](../sharepoint/featureproperties-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di valori di proprietà inclusi in un oggetto Feature quando viene distribuito in SharePoint.<br /><br /> È possibile includere un solo **elemento FeatureProperties.**|
|[File](../sharepoint/files-element.md)|Elemento **FileCollectionType facoltativo.**<br /><br /> Specifica i file da distribuire con l'SharePoint di progetto, ad esempio i file degli elementi funzionalità e l'output dei progetti non SharePoint dipendenti.<br /><br /> Includere un **elemento Files** o **ProjectItemFolder,** ma non entrambi.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Elemento **ProjectItemFolderType facoltativo.**<br /><br /> Rappresenta una cartella mappata.<br /><br /> Includere un **elemento Files** o **ProjectItemFolder,** ma non entrambi.|
|[SafeControls](../sharepoint/safecontrols-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di controlli ASPX e Web part designati come sicuri per l'accesso da parte di qualsiasi utente in qualsiasi pagina ASPX nel SharePoint web.<br /><br /> È possibile includere un solo **elemento SafeControls.**|

### <a name="parent-elements"></a>Elementi padre
 Nessuno.

## <a name="element-information"></a>Informazioni sull'elemento

|Proprietà|Valore|
|-|-|
|**Namespace**|http: \/ \/ schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Nome schema**|SharePoint Project schema dell'elemento|
|**File di convalida**|ProjectItemModelSchema.xsd|
|**Può essere vuoto**|No|

## <a name="see-also"></a>Vedere anche
[SharePoint rseference dello schema dell'elemento di progetto](../sharepoint/sharepoint-project-item-schema-reference.md)
