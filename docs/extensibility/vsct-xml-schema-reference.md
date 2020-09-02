---
title: Riferimento allo schema XML di VSCT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 923a0c4b64fcae3a409a2298d6d481f6e1bb14db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80697907"
---
# <a name="vsct-xml-schema-reference"></a>Riferimento XML Schema VSCT
Fornisce una tabella di elementi dello schema del compilatore della tabella dei comandi, con gli elementi figlio e gli attributi consentiti per ciascuno.

 Un file di configurazione della tabella dei comandi basato su XML (con estensione vsct) definisce gli elementi del comando forniti da un pacchetto VSPackage all'Integrated Development Environment (IDE). Questi elementi includono voci di menu, menu, barre degli strumenti e caselle combinate.

> [!NOTE]
> Il compilatore VSCT può eseguire un preprocessore nel file. vsct. Poiché si tratta in genere del preprocessore C++, è possibile definire le inclusioni e macro con la stessa sintassi usata nei file C++. Alcuni esempi sono forniti nel file con estensione vsct creato dalla creazione guidata **nuovo progetto** per un progetto VSPackage.

## <a name="optional-elements"></a>Elementi facoltativi
 Alcuni elementi VSCT sono facoltativi. Se `Parent` non viene specificato un argomento, Group_Undefined: 0 verranno implicite. Se `Icon` non viene specificato un argomento, guidOfficeIcon: msotcidNoIcon sarà implicito. Quando viene definito un tasto di scelta rapida, l'emulazione, che in genere è inutilizzata, è facoltativa.

 Gli elementi bitmap possono essere incorporati in fase di compilazione specificando la posizione della striscia bitmap nell' `href` argomento. La striscia bitmap viene copiata durante l'Unione anziché estratta dalle risorse della DLL. Quando `href` viene specificato un argomento, l' `usedList` argomento diventa facoltativo e tutti gli slot nella striscia bitmap vengono considerati utilizzati.

 Tutti i valori GUID e ID devono essere definiti usando nomi simbolici. Questi nomi possono essere definiti in file di intestazione o in \<Symbols> sezioni vsct. I nomi simbolici devono essere locali, inclusi tramite \<Include> elementi o a cui fanno riferimento \<Extern> gli elementi. Un nome simbolico viene importato da un file di intestazione specificato in un \<Extern> elemento se segue il modello semplice di #define valore del simbolo. Il valore può essere un altro simbolo finché il simbolo è stato definito in precedenza. Le definizioni GUID devono seguire il formato OLE o C++. I valori ID possono essere cifre decimali o cifre esadecimali precedute da 0x, come illustrato nelle righe seguenti:

- {6D484634-E53D-4a2c-ADCB-55145C9362C8}

- {0x6d484634, 0xe53d, 0x4a2c, {0xAD, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xC8}}

  È possibile usare i commenti XML, ma gli strumenti dell'interfaccia utente grafica (GUI) di round trip potrebbero eliminarli. Il contenuto degli \<Annotation> elementi è garantito per essere mantenuto indipendentemente dal formato.

## <a name="schema-hierarchy"></a>Gerarchia dello schema
 Un file con estensione vsct presenta gli elementi principali seguenti:

- [Elemento CommandTable](../extensibility/commandtable-element.md)

- [Extern (elemento)](../extensibility/extern-element.md)

- [Elemento include](../extensibility/include-element.md)

- [Definisci elemento](../extensibility/define-element.md)

- [Elemento Commands](../extensibility/commands-element.md)

- [Elemento CommandPlacements](../extensibility/commandplacements-element.md)

- [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)

- [Elemento Portatasti](../extensibility/keybindings-element.md)

- [Elemento UsedCommands](../extensibility/usedcommands-element.md)

- [Elemento padre](../extensibility/parent-element.md)

- [Icon (elemento)](../extensibility/icon-element.md)

- [Elemento Strings](../extensibility/strings-element.md)

- [Elemento del flag di comando](../extensibility/command-flag-element.md)

- [Symbols-elemento](../extensibility/symbols-element.md)

- [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Vedere anche
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing di comandi nei pacchetti VSPackage](../extensibility/internals/command-routing-in-vspackages.md)
