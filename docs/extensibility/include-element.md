---
title: L'elemento di inclusione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d77cca0b197f939170fc92f4d7d07bcadae8b53d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861801"
---
# <a name="include-element"></a>L'elemento di inclusione
L'elemento di inclusione specifica un file che può essere individuato fornito percorso per l'inserimento nel file corrente di inclusione.  Tutti i simboli e i tipi definiti diventerà parte del risultato compilato.

## <a name="syntax"></a>Sintassi

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|href|Obbligatorio. Il percorso del file di intestazione:<br /><br /> href="stdidcmd.h"|
|Condizione|Facoltativo. Visualizzare [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Nessuno.|Nessuno.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi, vale a dire, voci di menu, menu, barre degli strumenti e caselle combinate, ovvero che un pacchetto VSPackage fornisce all'IDE.|

## <a name="example"></a>Esempio

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>Vedere anche
- [File di Visual Studio comando table (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)