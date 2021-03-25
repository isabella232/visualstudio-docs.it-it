---
title: Elemento GuidSymbol | Microsoft Docs
description: "L'elemento GuidSymbol contiene il GUID della coppia GUID: ID che rappresenta un menu, un gruppo o un comando."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: eb683c99614797fa8b05eae87c758ec33f675c99
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057455"
---
# <a name="guidsymbol-element"></a>Elemento GuidSymbol
L' `GuidSymbol` elemento contiene il GUID della coppia GUID: ID che rappresenta un menu, un gruppo o un comando. L'ID deriva da un `IDSymbol` elemento nell' `GuidSymbol` elemento. L' `GuidSymbol` elemento dispone di un `name` attributo che fornisce un nome descrittivo per il GUID, contenuto nell' `value` attributo.

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
|[Elemento IDSymbol](../extensibility/idsymbol-element.md)|Contiene l'ID della coppia GUID: ID che rappresenta un menu, un gruppo o un comando.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Symbols-elemento](../extensibility/symbols-element.md)|Raggruppa `GuidSymbol` gli elementi in un file con *estensione vsct* .|

## <a name="remarks"></a>Commenti
 In genere, un file *. vsct* contiene tre `GuidSymbol` elementi nella relativa `Symbols` sezione, uno per il pacchetto stesso, uno per il set di comandi (la raccolta di menu, gruppi e comandi resi disponibili dal pacchetto) e uno per le bitmap che forniscono icone per i pulsanti e altri componenti visivi. Ogni `IDSymbol` elemento in un dato `GuidSymbol` elemento deve avere un univoco `value` . Tuttavia, `IDSymbol` gli elementi con valori identici possono esistere in un pacchetto purché abbiano elementi padre diversi.

## <a name="see-also"></a>Vedi anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
