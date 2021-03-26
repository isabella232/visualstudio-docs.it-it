---
title: Elemento include | Microsoft Docs
description: L'elemento include specifica un file che può trovarsi nel percorso di inclusione fornito per l'inserimento nel file corrente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fd64f897dc2a089a2e94f5e0c53e3ef116f7b385
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105082101"
---
# <a name="include-element"></a>Elemento include
L'elemento include specifica un file che può trovarsi nel percorso di inclusione fornito per l'inserimento nel file corrente.  Tutti i simboli e i tipi definiti diventeranno parte del risultato compilato.

## <a name="syntax"></a>Sintassi

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|href|Obbligatorio. Percorso del file di intestazione:<br /><br /> href = "Stdidcmd. h"|
|Condizione|facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|No.|No.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi, ovvero le voci di menu, i menu, le barre degli strumenti e le caselle combinate, fornite da un pacchetto VSPackage all'IDE.|

## <a name="example"></a>Esempio

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
