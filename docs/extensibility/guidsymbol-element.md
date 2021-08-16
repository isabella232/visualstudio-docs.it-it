---
title: Elemento GuidSymbol | Microsoft Docs
description: L'elemento GuidSymbol contiene il GUID della coppia GUID:ID che rappresenta un menu, un gruppo o un comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 712cdad6ae3e7cdd360b53b67ace9ee804509129fb3edfa5da96fac517a2ec9e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376495"
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
`GuidSymbol`L'elemento contiene il GUID della coppia GUID:ID che rappresenta un menu, un gruppo o un comando. L'ID proviene da `IDSymbol` un elemento `GuidSymbol` nell'elemento . `GuidSymbol`L'elemento ha un attributo che fornisce un nome `name` descrittivo per il GUID, contenuto `value` nell'attributo .

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
|Valore|Obbligatorio. GUID del simbolo GUID.|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contiene l'ID della coppia GUID:ID che rappresenta un menu, un gruppo o un comando.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento Symbols](../extensibility/symbols-element.md)|Raggruppa `GuidSymbol` gli elementi in un file con estensione *vsct.*|

## <a name="remarks"></a>Commenti
 In genere, un file *vsct* contiene tre elementi nella relativa sezione, uno per il pacchetto stesso, uno per il set di comandi (la raccolta di menu, gruppi e comandi che il pacchetto rende disponibile) e uno per le bitmap che forniscono icone per i pulsanti e altri componenti `GuidSymbol` `Symbols` visivi. Ogni `IDSymbol` elemento in un determinato elemento deve avere un elemento `GuidSymbol` `value` univoco. Tuttavia, gli elementi con valori identici possono esistere in un pacchetto purché `IDSymbol` hanno elementi padre diversi.

## <a name="see-also"></a>Vedi anche
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
