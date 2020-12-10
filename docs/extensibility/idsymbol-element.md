---
title: Elemento IDSymbol | Microsoft Docs
description: "L'elemento IDSymbol contiene l'ID della coppia GUID: ID che rappresenta un menu, un gruppo o un comando."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4feb477f8507bc3fe57e6db355538ab98ceeeaa
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995538"
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
L' `IDSymbol` elemento contiene l'ID della coppia GUID: ID che rappresenta un menu, un gruppo o un comando. Il GUID deriva dall'elemento padre `GuidSymbol` . L' `IDSymbol` elemento dispone di un `name` attributo che fornisce un nome descrittivo per l'ID, contenuto nell' `value` attributo.

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
|Valore|Obbligatorio. Valore ID numerico del simbolo ID.|

### <a name="child-elements"></a>Elementi figlio
 Nessuno.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento GuidSymbol](../extensibility/guidsymbol-element.md)|Contiene il GUID della coppia GUID: ID che rappresenta un menu, un gruppo o un comando. Raggruppa gli elementi `IDSymbol`.|

## <a name="remarks"></a>Commenti
 Ogni `IDSymbol` elemento in un dato `GuidSymbol` elemento deve avere un univoco `value` . Tuttavia, `IDSymbol` gli elementi con valori identici possono esistere in un pacchetto purché abbiano elementi padre diversi.

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
