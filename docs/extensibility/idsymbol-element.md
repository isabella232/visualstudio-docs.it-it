---
title: Elemento IDSymbol | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d88acb221abfc26c45c9002abb92f704936334b
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500381"
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
Il `IDSymbol` elemento contiene l'ID della coppia GUID: ID che rappresenta un menu, gruppo o comando. Il GUID viene fornito dall'elemento padre `GuidSymbol` elemento. Il `IDSymbol` elemento ha un `name` attributo che fornisce un nome descrittivo per l'ID, che è contenuto nel `value` attributo.  
  
## <a name="syntax"></a>Sintassi  
  
```xml  
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
 [File di Visual Studio comando table (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)