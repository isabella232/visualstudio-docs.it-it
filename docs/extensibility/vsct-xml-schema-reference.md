---
title: Riferimento allo schema XML di VSCT Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697907"
---
# <a name="vsct-xml-schema-reference"></a>Riferimento allo schema XML VSCT
Fornisce una tabella di elementi dello schema del compilatore della tabella dei comandi, con gli elementi figlio consentiti e gli attributi per ognuno.

 Un file di configurazione della tabella dei comandi basata su XML (con estensione vsct) definisce gli elementi di comando che un pacchetto VSPackage fornisce all'ambiente di sviluppo integrato (IDE). Questi elementi includono voci di menu, menu, barre degli strumenti e caselle combinate.

> [!NOTE]
> Il compilatore VSCT può eseguire un preprocessore sul file vsct. Dal caso in genere si tratti del preprocessore di C, è possibile definire i componenti aggiuntivi e le macro con la stessa sintassi utilizzata nei file di C. Esempi di questo sono forniti nel file vsct che la creazione guidata **nuovo progetto** crea per un progetto VSPackage.

## <a name="optional-elements"></a>Elementi opzionali
 Alcuni elementi VSCT sono facoltativi. Se `Parent` non viene specificato un argomento, Group_Undefined:0 sarà implicito. Se `Icon` non viene specificato un argomento, guidOfficeIcon:msotcidNoIcon sarà implicito. Quando viene definito un tasto di scelta rapida, l'emulazione, che in genere non viene utilizzata, è facoltativa.

 Gli elementi bitmap possono essere incorporati in fase di compilazione specificando la posizione della striscia bitmap nell'argomento. `href` La striscia bitmap viene copiata durante l'unione anziché estratta dalle risorse della DLL. Quando `href` viene fornito un `usedList` argomento, l'argomento diventa facoltativo e tutti gli slot nella striscia bitmap vengono considerati utilizzati.

 Tutti i valori GUID e ID devono essere definiti utilizzando nomi simbolici. Questi nomi possono essere definiti in \<file di intestazione o in simboli VSCT> sezioni. I nomi simbolici devono \<essere locali, inclusi tramite Gli elementi Include> o a cui fanno riferimento \<Extern> elementi. Un nome simbolico viene importato da \<un file di intestazione specificato in un elemento di> Extern se segue il modello semplice di #define SYMBOL VALUE. Il valore può essere un altro simbolo, purché tale simbolo sia stato definito in precedenza. Le definizioni dei GUID devono seguire il formato OLE o C. I valori ID possono essere cifre decimali o cifre esadecimali precedute da 0x, come illustrato nelle righe seguenti:

- 6D484634-E53D-4a2c-ADCB-55145C9362C8

- 0x6d484634, 0xe53d, 0x4a2c, 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8

  È possibile utilizzare commenti XML, ma gli strumenti dell'interfaccia utente grafica (GUI) di andata e ritorno potrebbero eliminarli. Il contenuto \<degli elementi di Annotation> è garantito per essere mantenuto indipendentemente dal formato.

## <a name="schema-hierarchy"></a>Gerarchia dello schema
 Un file vsct ha i seguenti elementi principali.

- [Elemento CommandTable](../extensibility/commandtable-element.md)

- [Elemento Extern](../extensibility/extern-element.md)

- [Includi elemento](../extensibility/include-element.md)

- [Definisci elemento](../extensibility/define-element.md)

- [Elemento Commands](../extensibility/commands-element.md)

- [CommandPlacements (elemento)](../extensibility/commandplacements-element.md)

- [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)

- [Elemento KeyBindings](../extensibility/keybindings-element.md)

- [UsedCommands (elemento)](../extensibility/usedcommands-element.md)

- [Elemento padre](../extensibility/parent-element.md)

- [Elemento icona](../extensibility/icon-element.md)

- [Elemento Strings](../extensibility/strings-element.md)

- [Elemento Flag di comando](../extensibility/command-flag-element.md)

- [Elemento Symbols](../extensibility/symbols-element.md)

- [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md)

## <a name="see-also"></a>Vedere anche
- [Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Routing dei comandi nei pacchetti VSPackageCommand routing in VSPackages](../extensibility/internals/command-routing-in-vspackages.md)
