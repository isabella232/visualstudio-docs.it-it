---
title: Proprietà Extern Element . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2cf6f9db77abaa7034af8d074b9833a4c1560f07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711494"
---
# <a name="extern-element"></a>Elemento Extern
L'elemento Extern fa riferimento a qualsiasi file di intestazione esterna (*.h*) da unire al file *vsct* in fase di compilazione. I file da unire devono trovarsi nel percorso Include specificato al compilatore VSCT o a cui fa riferimento un [elemento Include](../extensibility/include-element.md). I file possono essere altri file *vsct* o file di intestazione di C.

 Le definizioni nei file di intestazione devono avere il formato "#define [Simbolo] [Valore]" Il valore può essere un altro simbolo se è definito in precedenza. Le definizioni possono essere utilizzate nelle istruzioni condizionali degli elementi di comando. Qualsiasi simbolo non effettivamente utilizzato verrà eliminato.

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
|href|Obbligatorio. Percorso del file di intestazione:<br /><br /> href: "stdidcmd.h"|
|Condizione|Facoltativa. Consultate [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|Linguaggio|Facoltativa. La lingua predefinita [ \<](../extensibility/strings-element.md) di tutte le stringhe>gli elementi nella tabella dei comandi:<br /><br /> lingua: "en-us"|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|No.|No.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi, ovvero voci di menu, menu, barre degli strumenti e caselle combinate, che un VSPackage fornisce all'IDE.|

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
- [Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)
