---
title: Elemento IDSymbol | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7db4e686b5e105b0ea0aa80783137093679d4cad
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965689"
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
