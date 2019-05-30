---
title: Elemento GuidSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bebcec561f915bd8223d0adc183293a1760c261d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342217"
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
Il `GuidSymbol` elemento contiene il GUID della coppia GUID: ID che rappresenta un menu, gruppo o comando. L'ID proviene da un' `IDSymbol` elemento il `GuidSymbol` elemento. Il `GuidSymbol` elemento ha un `name` attributo che fornisce un nome descrittivo per il GUID, contenuta nel `value` attributo.

## <a name="syntax"></a>Sintassi

```xml
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
|[Elemento Symbols](../extensibility/symbols-element.md)|I gruppi `GuidSymbol` elementi in un *vsct* file.|

## <a name="remarks"></a>Note
 In genere, un *vsct* file contiene tre `GuidSymbol` elementi nel relativo `Symbols` sezione, uno per il pacchetto stesso, uno per il set di comandi (la raccolta di menu, gruppi e i comandi che rende disponibile il pacchetto), e uno per le mappe di bit che forniscono le icone per i pulsanti e altri componenti visivi. Ogni `IDSymbol` elemento in un determinato `GuidSymbol` elemento deve avere un valore univoco `value`. Tuttavia, `IDSymbol` possono essere presenti in un pacchetto di elementi che hanno valori identici purché hanno elementi padre diversi.

## <a name="see-also"></a>Vedere anche
- [File di Visual Studio comando table (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)