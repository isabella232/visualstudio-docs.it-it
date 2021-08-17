---
title: Elemento Extern | Microsoft Docs
description: L'elemento Extern fa riferimento a qualsiasi file di intestazione esterna (con estensione h) da unire al file vsct in fase di compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9a9fa1e2979aefa533566ccc4a964c47bde3c701
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070262"
---
# <a name="extern-element"></a>Elemento Extern
L'elemento Extern fa riferimento a qualsiasi file di intestazione esterna ( con estensione *h*) da unire al file *vsct* in fase di compilazione. I file da unire devono essere nel percorso Include fornito al compilatore VSCT o a cui fa riferimento un [elemento Include.](../extensibility/include-element.md) I file possono essere altri *file con estensione vsct* o file di intestazione C++.

 Le definizioni nei file di intestazione devono essere nel formato "#define [Simbolo] [Valore]" Il valore può essere un altro simbolo se è definito in precedenza. Le definizioni possono essere usate nelle istruzioni condizionali degli elementi di comando. Qualsiasi simbolo non effettivamente usato verrà eliminato.

 Elemento CommandTable Extern

## <a name="syntax"></a>Sintassi

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|href|Obbligatorio. Percorso del file di intestazione:<br /><br /> href="stdidcmd.h"|
|Condition|facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|Linguaggio|facoltativo. Lingua predefinita di tutti [\<Strings>](../extensibility/strings-element.md) gli elementi nella tabella dei comandi:<br /><br /> language="en-us"|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|No.|No.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano comandi, ovvero voci di menu, menu, barre degli strumenti e caselle combinate, forniti da un vspackage all'IDE.|

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
- [Visual Studio file di tabella dei comandi (con estensione vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
