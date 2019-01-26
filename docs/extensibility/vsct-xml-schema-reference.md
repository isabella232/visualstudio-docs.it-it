---
title: Riferimento allo Schema XML VSCT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio command table configuration files (VSCT), XML schema
- VSCT XML schema elements
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a6f6860c64094fc84e5ebe64ede4c6e38ff7d0f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993937"
---
# <a name="vsct-xml-schema-reference"></a>Riferimento allo schema XML VSCT
Fornisce una tabella di elementi dello schema di comando del compilatore di tabella, con l'elemento figlio consentito gli elementi e attributi per ognuna.  
  
 Un file di configurazione (con estensione vsct) tabella comando basato su XML definisce gli elementi di comando che un pacchetto VSPackage fornisce all'ambiente di sviluppo integrato (IDE). Questi elementi includono voci di menu, menu, barre degli strumenti e caselle combinate.  
  
> [!NOTE]
>  Il compilatore VSCT eseguibili del preprocessore sul file con estensione vsct. Poiché si tratta in genere include di C++ per il preprocessore, che è possibile definire e macro che hanno la stessa sintassi utilizzata nel file di C++. Nel file vsct vengono forniti esempi di questo file che il **nuovo progetto** procedura guidata crea un progetto di VSPackage.  
  
## <a name="optional-elements"></a>Elementi facoltativi  
 Alcuni elementi VSCT sono facoltativi. Se un `Parent` argomento non è specificato, verrà implicita Group_Undefined:0. Se un `Icon` argomento non è specificato, verrà implicita guidOfficeIcon:msotcidNoIcon. Quando viene definito un tasto di scelta rapida, l'emulazione, che non viene utilizzato in genere, è facoltativo.  
  
 Gli elementi mappa di bit possono essere incorporati in fase di compilazione specificando il percorso della striscia di bitmap nel `href` argomento. Striscia di bitmap viene copiata durante l'unione anziché estratte dalle risorse della DLL. Quando un `href` argomento è specificato, il `usedList` argomento diventa facoltativo e tutti gli slot nella striscia di bitmap sono considerati utilizzato.  
  
 Tutti i valori GUID e ID devono essere definiti con nomi simbolici. Questi nomi possono essere definiti nel file di intestazione o nel VSCT \<simboli > sezioni. I nomi simbolici devono essere locali, inclusi attraverso \<inclusione > elementi, o fa \<Extern > elementi. Un nome simbolico viene importato da un file di intestazione specificato in un \<Extern > elemento se segue il modello semplice di #define il valore di simbolo. Il valore può essere un altro simbolo, purché tale simbolo è stato definito in precedenza. Le definizioni di GUID devono seguire nel formato OLE o C++. I valori di ID possono essere cifre decimali o esadecimali che sono preceduti da 0x, come illustrato nelle righe seguenti:  
  
- {6D484634-E53D-4a2c-ADCB-55145C9362C8}  
  
- { 0x6d484634, 0xe53d, 0x4a2c, { 0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8 } }  
  
  Commenti in formato XML può essere usati, ma potrebbero rimuovere tali strumenti dell'interfaccia utente grafica di andata e ritorno. Il contenuto di \<Annotation > gli elementi sono garantiti a essere gestito indipendentemente dal formato.  
  
## <a name="schema-hierarchy"></a>Gerarchia dello schema  
 Un file con estensione vsct presenta gli elementi principali seguenti:  
  
 [Elemento CommandTable](../extensibility/commandtable-element.md)  
  
 [Elemento extern](../extensibility/extern-element.md)  
  
 [L'elemento di inclusione](../extensibility/include-element.md)  
  
 [Definire l'elemento](../extensibility/define-element.md)  
  
 [Elemento Commands](../extensibility/commands-element.md)  
  
 [Elemento CommandPlacements](../extensibility/commandplacements-element.md)  
  
 [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)  
  
 [Elemento KeyBindings](../extensibility/keybindings-element.md)  
  
 [Elemento UsedCommands](../extensibility/usedcommands-element.md)  
  
 [Elemento padre](../extensibility/parent-element.md)  
  
 [Elemento Icon](../extensibility/icon-element.md)  
  
 [Elemento Strings](../extensibility/strings-element.md)  
  
 [Elemento Commandflag](../extensibility/command-flag-element.md)  
  
 [Elemento Symbols](../extensibility/symbols-element.md)  
  
 [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routing dei comandi nei pacchetti VSPackage](../extensibility/internals/command-routing-in-vspackages.md)