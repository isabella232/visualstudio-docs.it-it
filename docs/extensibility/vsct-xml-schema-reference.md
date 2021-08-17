---
title: Informazioni di riferimento su VSCT XML Schema | Microsoft Docs
description: Gli articoli di riferimento sullo schema XML VSCT descrivono gli elementi dello schema del compilatore di tabelle comandi, con gli elementi figlio e gli attributi consentiti per ognuno.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f3c1a09a7000b19980c14cd71fa02b600a2de9aea9fd514c1caa8e28a02307c1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400504"
---
# <a name="vsct-xml-schema-reference"></a>Informazioni di riferimento sullo schema XML VSCT
Fornisce una tabella di elementi dello schema del compilatore di tabelle comandi, con gli elementi figlio e gli attributi consentiti per ognuno.

 Un file di configurazione della tabella dei comandi basato su XML (con estensione vsct) definisce gli elementi di comando forniti da un pacchetto VSPackage all'ambiente di sviluppo integrato (IDE). Questi elementi includono voci di menu, menu, barre degli strumenti e caselle combinate.

> [!NOTE]
> Il compilatore VSCT può eseguire un preprocessore nel file con estensione vsct. Poiché si tratta in genere del preprocessore C++, è possibile definire le macro includes e con la stessa sintassi usata nei file C++. Esempi di questo tipo vengono forniti nel file con estensione vsct creato dalla procedura guidata **Project** per un progetto VSPackage.

## <a name="optional-elements"></a>Elementi facoltativi
 Alcuni elementi VSCT sono facoltativi. Se non `Parent` viene specificato un argomento, Group_Undefined:0 sarà implicito. Se non `Icon` viene specificato un argomento, guidOfficeIcon:msotcidNoIcon verrà implicito. Quando viene definito un tasto di scelta rapida, l'emulazione, in genere inutilizzata, è facoltativa.

 Gli elementi bitmap possono essere incorporati in fase di compilazione specificando il percorso della striscia bitmap `href` nell'argomento . La striscia bitmap viene copiata durante l'unione anziché estratta dalle risorse della DLL. Quando viene `href` fornito un argomento, l'argomento diventa facoltativo e tutti gli slot nella striscia `usedList` bitmap vengono considerati usati.

 Tutti i valori GUID e ID devono essere definiti usando nomi simbolici. Questi nomi possono essere definiti nei file di intestazione o nelle sezioni di \<Symbols> VSCT. I nomi simbolici devono essere locali, inclusi tramite \<Include> elementi o a cui fanno riferimento gli \<Extern> elementi. Un nome simbolico viene importato da un file di intestazione specificato in un elemento se segue il modello semplice di #define \<Extern> SYMBOL VALUE. Il valore può essere un altro simbolo, purché tale simbolo sia stato definito in precedenza. Le definizioni GUID devono seguire il formato OLE o C++. I valori ID possono essere cifre decimali o cifre esadecimali precedute da 0x, come illustrato nelle righe seguenti:

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } }

  È possibile usare commenti XML, ma è possibile che gli strumenti dell'interfaccia utente grafica (GUI) di round trip li scartino. Il contenuto degli \<Annotation> elementi viene mantenuto indipendentemente dal formato.

## <a name="schema-hierarchy"></a>Gerarchia dello schema
 Un file con estensione vsct include gli elementi principali seguenti.

- [Elemento CommandTable](../extensibility/commandtable-element.md)

- [Elemento Extern](../extensibility/extern-element.md)

- [Elemento Include](../extensibility/include-element.md)

- [Elemento Define](../extensibility/define-element.md)

- [Elemento Commands](../extensibility/commands-element.md)

- [Elemento CommandPlacements](../extensibility/commandplacements-element.md)

- [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)

- [Elemento KeyBindings](../extensibility/keybindings-element.md)

- [Elemento UsedCommands](../extensibility/usedcommands-element.md)

- [Elemento padre](../extensibility/parent-element.md)

- [Elemento Icon](../extensibility/icon-element.md)

- [Elemento Strings](../extensibility/strings-element.md)

- [Elemento Command Flag](../extensibility/command-flag-element.md)

- [Elemento Symbols](../extensibility/symbols-element.md)

- [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Vedi anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing dei comandi in VSPackage](../extensibility/internals/command-routing-in-vspackages.md)
