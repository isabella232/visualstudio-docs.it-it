---
title: Elemento IDSymbol | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f3ab239c85fbf3e9ebc83825750b78a1e6fdbf7f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518946"
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [elemento IDSymbol](https://docs.microsoft.com/visualstudio/extensibility/idsymbol-element).  
  
Il `IDSymbol` elemento contiene l'ID della coppia GUID: ID che rappresenta un menu, gruppo o comando. Il GUID viene fornito dall'elemento padre `GuidSymbol` elemento. Il `IDSymbol` elemento ha un `name` attributo che fornisce un nome descrittivo per l'ID, che è contenuto nel `value` attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<IDSymbol name=ElementName value="0x0010" />  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|name|Obbligatorio. Nome del simbolo ID.|  
|predefinito|Obbligatorio. Valore ID numerico del simbolo ID.|  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento GuidSymbol](../extensibility/guidsymbol-element.md)|Contiene il GUID della coppia GUID: ID che rappresenta un menu, gruppo o comando. Raggruppa gli elementi `IDSymbol`.|  
  
## <a name="remarks"></a>Note  
 Ogni `IDSymbol` elemento in un determinato `GuidSymbol` elemento deve avere un valore univoco `value`. Tuttavia, `IDSymbol` possono essere presenti in un pacchetto di elementi che hanno valori identici purché hanno elementi padre diversi.  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

