---
title: Elemento GuidSymbol | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59068a9ac9f952b5370681b3684ce4234354afc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711124"
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

## <a name="remarks"></a>Osservazioni
 In genere, un file *. vsct* contiene tre `GuidSymbol` elementi nella relativa `Symbols` sezione, uno per il pacchetto stesso, uno per il set di comandi (la raccolta di menu, gruppi e comandi resi disponibili dal pacchetto) e uno per le bitmap che forniscono icone per i pulsanti e altri componenti visivi. Ogni `IDSymbol` elemento in un dato `GuidSymbol` elemento deve avere un univoco `value` . Tuttavia, `IDSymbol` gli elementi con valori identici possono esistere in un pacchetto purché abbiano elementi padre diversi.

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
