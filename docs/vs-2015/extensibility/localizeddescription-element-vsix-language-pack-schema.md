---
title: Elemento LocalizedDescription (schema del Language Pack VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 766a1732-bbaf-4875-b276-feb42169633a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b4eb077ba8c957466568967804487929254117e
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114191"
---
# <a name="localizeddescription-element-vsix-language-pack-schema"></a>Elemento LocalizedDescription (schema del Language Pack VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obbligatorio. Fornisce una descrizione localizzata dell'estensione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<LocalizedDescription>Localized description of the extension</LocalizedDescription>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|nessuno||  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|nessuno||  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Obbligatorio. Fornisce l'elemento radice per un Language Pack VSIX.|  
  
## <a name="text-value"></a>Valore di testo  
 Obbligatorio. Descrizione testuale dell'estensione nella lingua di destinazione.  
  
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
        Non applicabile
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sullo schema del Language Pack VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)   
 [Riferimento allo schema di estensione VSIX 1,0](/previous-versions/dd393700(v=vs.110))
