---
title: Elemento extern | Microsoft Docs
description: L'elemento extern fa riferimento a qualsiasi file di intestazione esterna (. h) da unire con il file vsct in fase di compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5771dbc1c6b17b0f488d42c30a036ff1d90a5a18
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074990"
---
# <a name="extern-element"></a>Extern (elemento)
L'elemento extern fa riferimento a qualsiasi file di intestazione esterna (*. h*) da unire con il file *vsct* in fase di compilazione. I file da unire devono trovarsi nel percorso di inclusione assegnato al compilatore VSCT o a cui fa riferimento un [elemento include](../extensibility/include-element.md). I file possono essere altri file con *estensione vsct* o file di intestazione C++.

 Le definizioni nei file di intestazione devono essere nel formato "#define [Symbol] [valore]". il valore può essere un altro simbolo se è stato definito in precedenza. Le definizioni possono essere utilizzate nelle istruzioni condizionali degli elementi di comando. Qualsiasi simbolo non effettivamente usato verrà rimosso.

 Elemento extern elemento CommandTable

## <a name="syntax"></a>Sintassi

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|href|Obbligatorio. Percorso del file di intestazione:<br /><br /> href = "Stdidcmd. h"|
|Condizione|facoltativo. Vedere [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|Linguaggio|facoltativo. Lingua predefinita di tutti [\<Strings>](../extensibility/strings-element.md) gli elementi nella tabella dei comandi:<br /><br /> lingua = "en-US"|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|No.|No.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi, ovvero le voci di menu, i menu, le barre degli strumenti e le caselle combinate, fornite da un pacchetto VSPackage all'IDE.|

## <a name="example"></a>Esempio

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>Vedere anche
- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
