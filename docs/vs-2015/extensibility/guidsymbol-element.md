---
title: Elemento GuidSymbol | Microsoft Docs
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
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4e6e5bab37e9a0b9f0ffdf03778532d9657539c6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528040"
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [elemento GuidSymbol](https://docs.microsoft.com/visualstudio/extensibility/guidsymbol-element).  
  
Il `GuidSymbol` elemento contiene il GUID della coppia GUID: ID che rappresenta un menu, gruppo o comando. L'ID proviene da un' `IDSymbol` elemento il `GuidSymbol` elemento. Il `GuidSymbol` elemento ha un `name` attributo che fornisce un nome descrittivo per il GUID, contenuta nel `value` attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|name|Obbligatorio. Nome del simbolo GUID.|  
|predefinito|Obbligatorio. GUID del simbolo GUID.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contiene l'ID della coppia GUID: ID che rappresenta un menu, gruppo o comando.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento Symbols](../extensibility/symbols-element.md)|Gruppi `GuidSymbol` elementi in un file con estensione vsct.|  
  
## <a name="remarks"></a>Note  
 In genere, un file con estensione vsct contiene tre `GuidSymbol` elementi nel relativo `Symbols` sezione, uno per il pacchetto stesso, uno per il set di comandi (la raccolta di menu, gruppi e i comandi che rende disponibile il pacchetto) e uno per le mappe di bit che forniscono icone per i pulsanti e altri componenti visivi. Ogni `IDSymbol` elemento in un determinato `GuidSymbol` elemento deve avere un valore univoco `value`. Tuttavia, `IDSymbol` possono essere presenti in un pacchetto di elementi che hanno valori identici purché hanno elementi padre diversi.  
  
## <a name="see-also"></a>Vedere anche  
 [File Visual Studio Command Table (VSCT)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

