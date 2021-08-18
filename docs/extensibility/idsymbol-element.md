---
title: Elemento IDSymbol | Microsoft Docs
description: L'elemento IDSymbol contiene l'ID della coppia GUID:ID che rappresenta un menu, un gruppo o un comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 513033b2db2cbf222c7835679ad36e00b91887b6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086898"
---
# <a name="idsymbol-element"></a>Elemento IDSymbol
`IDSymbol`L'elemento contiene l'ID della coppia GUID:ID che rappresenta un menu, un gruppo o un comando. Il GUID proviene dall'elemento `GuidSymbol` padre. `IDSymbol`L'elemento ha un attributo che fornisce un nome `name` descrittivo per l'ID, contenuto `value` nell'attributo .

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
|[Elemento GuidSymbol](../extensibility/guidsymbol-element.md)|Contiene il GUID della coppia GUID:ID che rappresenta un menu, un gruppo o un comando. Raggruppa gli elementi `IDSymbol`.|

## <a name="remarks"></a>Commenti
 Ogni `IDSymbol` elemento in un determinato elemento deve avere un `GuidSymbol` `value` univoco. Tuttavia, gli elementi con valori identici possono esistere in un pacchetto purché `IDSymbol` hanno elementi padre diversi.

## <a name="see-also"></a>Vedi anche
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
