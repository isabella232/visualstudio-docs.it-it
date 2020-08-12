---
title: Elemento VSIXLanguagePack (schema del Language Pack VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd3ed1477d1c4d345e5fc6f6496d12044d4af244
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114232"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Elemento VSIXLanguagePack (schema del Language Pack VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obbligatorio. Fornisce l'elemento radice per un Language Pack VSIX. Il Language Pack VSIX fornisce le informazioni di installazione localizzate per un pacchetto VSIX.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`xmlns`|Lo spazio dei nomi XML in cui è definito lo schema del Language Pack VSIX.|  
  
## <a name="xmlns-attribute"></a>Attributo xmlns  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Obbligatorio. Percorso del file che definisce lo schema per i Language Pack.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Obbligatorio. Nome localizzato dell'estensione da installare.|  
|[Elemento LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Obbligatorio. Descrizione localizzata dell'estensione da installare.|  
|[Elemento MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|facoltativo. Collegamento alle informazioni localizzate sull'estensione.|  
|[Elemento License](../extensibility/license-element-vsix-language-pack-schema.md)|facoltativo. Percorso di una versione localizzata del file di licenza per l'estensione.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|nessuno||  
  
## <a name="element-information"></a>Informazioni sull'elemento  

:::row:::
    :::column:::
        Spazio dei nomi
    :::column-end:::
    :::column:::
        `http://schemas.microsoft.com/developer/vsx-schema-lp/2010`
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Schema Name
    :::column-end:::
    :::column:::
        Schema del Language Pack VSIX
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        File di convalida
    :::column-end:::
    :::column:::
        VSIXLanguagePackSchema. xsd
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Può essere vuoto
    :::column-end:::
    :::column:::
        No
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>Vedere anche  
 Informazioni di [riferimento sullo schema del Language Pack di VSX](../extensibility/vsx-language-pack-schema-reference.md) [localizzazione dei pacchetti VSIX](../extensibility/localizing-vsix-packages.md) [estensione VSIX schema 1,0](/previous-versions/dd393700(v=vs.110))
