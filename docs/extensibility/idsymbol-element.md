---
title: Proprietà IDSymbol . Documenti Microsoft
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
ms.openlocfilehash: d02a26a6874165738d917a14986d16d142c01915
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710368"
---
# <a name="idsymbol-element"></a>IdSymbol (elemento)
L'elemento `IDSymbol` contiene l'ID della coppia GUID:ID che rappresenta un menu, un gruppo o un comando. Il GUID proviene `GuidSymbol` dall'elemento padre. L'elemento `IDSymbol` `name` dispone di un attributo che fornisce un `value` nome descrittivo per l'ID, che è contenuto nell'attributo.

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
 No.

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[GuidSymbol (elemento)](../extensibility/guidsymbol-element.md)|Contiene il GUID della coppia GUID:ID che rappresenta un menu, un gruppo o un comando. Raggruppa gli elementi `IDSymbol`.|

## <a name="remarks"></a>Osservazioni
 Ogni `IDSymbol` elemento in `GuidSymbol` un determinato `value`elemento deve avere un oggetto . Tuttavia, `IDSymbol` gli elementi con valori identici possono esistere in un pacchetto, purché abbiano elementi padre diversi.

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
