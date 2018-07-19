---
title: Elemento ProjectItem | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ca0c295410caffb476d6c1e796864c47520a2f56
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119931"
---
# <a name="projectitem-element"></a>ProjectItem (elemento)
  Rappresenta un elemento del progetto SharePoint. Questo elemento l'elemento radice obbligatorio del *spdata* file.  
  
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
|**DefaultFile**|Facoltativo **xs: string** attributo.<br /><br /> Il percorso relativo, incluso il nome di file, del file che viene aperto nell'editor di Visual Studio quando si apre l'elemento del progetto SharePoint in **Esplora soluzioni**. Il percorso è relativo rispetto alla cartella che contiene il *spdata* file.|  
|**FeatureReceiverClass**|Facoltativo **xs: String** attributo.<br /><br /> Il nome completo di una classe del ricevitore di funzionalità per questo elemento di progetto SharePoint. Per altre informazioni sui ricevitori di funzionalità, vedere [fornire le informazioni di creazione di pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).|  
|**FeatureReceiverAssembly**|Facoltativo **xs: String** attributo.<br /><br /> Specifica il nome completo di un assembly che definisce un ricevitore di funzionalità per questo elemento di progetto SharePoint. Per altre informazioni sui ricevitori di funzionalità, vedere [fornire le informazioni di creazione di pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md). Per altre informazioni sui nomi di assembly completo, vedere [i nomi degli Assembly](/dotnet/framework/app-domains/assembly-names).|  
|**SupportedTrustLevels**|Facoltativo **xs: String** attributo.<br /><br /> Specifica i livelli di attendibilità che supporta questo elemento del progetto SharePoint. Questo valore può essere uno delle seguenti stringhe: creata mediante sandbox, FullTrust, o tutti. Il valore All specifica sia Sandboxed e FullTrust.<br /><br /> In un tipo di elemento di progetto SharePoint personalizzato, il valore di questo attributo corrisponde al valore assegnato per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> proprietà nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> (metodo). Se si specifica un valore diverso per questo attributo, Visual Studio sovrascrive il valore in modo che specifichi lo stesso livello di attendibilità specificato nella <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> proprietà.|  
|**SupportedDeploymentScopes**|Facoltativo **xs: String** attributo.<br /><br /> Specifica gli ambiti di distribuzione che supporta questo elemento del progetto SharePoint. Questo valore è una stringa delimitata da virgole costituita da uno o più delle seguenti stringhe: Farm, sito, Web, WebApplication o pacchetto. Ad esempio: `Web, Site`<br /><br /> In un tipo di elemento di progetto SharePoint personalizzato, il valore di questo attributo corrisponde al valore assegnato per il <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> proprietà nell'implementazione del <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> (metodo). Se si specifica un valore diverso per questo attributo, Visual Studio sovrascrive il valore in modo che specifichi lo stesso livello di attendibilità specificato nella <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> proprietà.|  
|**Type**|Obbligatorio **xs: String** attributo.<br /><br /> L'identificatore per l'elemento del progetto SharePoint. In un tipo di elemento di progetto SharePoint personalizzato, l'identificatore corrisponde alla stringa che viene passato al <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>. Per altre informazioni, vedere [procedura: definire un tipo di elemento di progetto SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).<br /><br /> Per un elenco degli identificatori per gli elementi del progetto SharePoint predefiniti inclusi in Visual Studio, vedere [elementi di progetto SharePoint estendere](../sharepoint/extending-sharepoint-project-items.md).|  
  
### <a name="child-elements"></a>Elementi figlio
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di elementi di dati personalizzati associati con l'elemento del progetto SharePoint.<br /><br /> È possibile includere una sola **ExtensionData** elemento.|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di valori di proprietà che sono inclusi in una funzione quando viene distribuito in SharePoint.<br /><br /> È possibile includere una sola **FeatureProperties** elemento.|  
|[File](../sharepoint/files-element.md)|Facoltativo **FileCollectionType** elemento.<br /><br /> Specifica i file da distribuire con l'elemento del progetto SharePoint, ad esempio i file di elemento di funzionalità e l'output dei progetti di SharePoint non dipendente.<br /><br /> Includere un **file** o una **ProjectItemFolder** elemento, ma non entrambi.|  
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|Facoltativo **ProjectItemFolderType** elemento.<br /><br /> Rappresenta una cartella mappata.<br /><br /> Includere un **file** o una **ProjectItemFolder** elemento, ma non entrambi.|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Elemento facoltativo.<br /><br /> Rappresenta una raccolta di controlli ASPX e Web part che sono definiti come sicuri per tutti gli utenti accedere in qualsiasi pagina ASPX nel sito di SharePoint.<br /><br /> È possibile includere una sola **SafeControls** elemento.|  
  
### <a name="parent-elements"></a>Elementi padre
 Nessuno.  
  
## <a name="element-information"></a>Informazioni sull'elemento
  
|||  
|-|-|  
|**Spazio dei nomi**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Nome dello schema**|Schema degli elementi di progetto SharePoint|  
|**File di convalida**|ProjectItemModelSchema.xsd|  
|**Può essere vuoto**|No|  
  
## <a name="see-also"></a>Vedere anche
[SharePoint progetto elemento schema rseference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
