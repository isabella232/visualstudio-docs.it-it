---
title: Elemento extern | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d62d52d490994889f7e9186fb74ea148cb52a06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62911895"
---
# <a name="extern-element"></a>Elemento extern
L'elemento Extern fa riferimento a una delle intestazioni esterne (*h*) file da unire con i *con estensione vsct* file in fase di compilazione. I file da unire devono trovarsi nel percorso di inclusione specificato per il compilatore VSCT oppure fa riferimento un' [elemento Include](../extensibility/include-element.md). I file potrebbero essere loro *vsct* file o file di intestazione C++.

 Le definizioni nel file di intestazione devono essere nel formato "#define [simbolo] [valore]" il valore può essere un altro simbolo, se è definito in precedenza. Le definizioni possono essere utilizzate nelle istruzioni condizionali di elementi di comando. Qualsiasi simbolo non usato effettivamente verrà rimosse.

 Elemento Extern elemento CommandTable

## <a name="syntax"></a>Sintassi

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Attributi ed elementi
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|href|Obbligatorio. Il percorso del file di intestazione:<br /><br /> href="stdidcmd.h"|
|Condizione|Facoltativo. Visualizzare [attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|language|Facoltativo. La lingua predefinita di tutte le [ \<stringhe >](../extensibility/strings-element.md) elementi della tabella comandi:<br /><br /> language="en-us"|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Descrizione|
|-------------|-----------------|
|Nessuno.|Nessuno.|

### <a name="parent-elements"></a>Elementi padre

|Elemento|Descrizione|
|-------------|-----------------|
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi, vale a dire, voci di menu, menu, barre degli strumenti e caselle combinate, ovvero che un pacchetto VSPackage fornisce all'IDE.|

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
- [File di Visual Studio comando table (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)