---
title: GUID e ID dei Visual Studio di | Microsoft Docs
description: Informazioni su come individuare i valori GUID e ID dei comandi inclusi nell Visual Studio ide (Integrated Development Environment).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b06c4b20e4972b8ee697758c1c0b88679f2a37f3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634563"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUID e ID dei Visual Studio seguenti
I valori GUID e ID dei comandi inclusi nell'ambiente di sviluppo integrato (IDE) di Visual Studio sono definiti in file con estensione vsct installati come parte di Visual Studio SDK. Per altre informazioni, vedere Comandi, menu e gruppi definiti [dall'IDE.](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Per altre informazioni su come usare gli oggetti IDE definiti nei file con estensione *vsct,* vedere [Estendere menu e comandi.](../../extensibility/extending-menus-and-commands.md)

## <a name="find-a-command-definition"></a>Trovare una definizione di comando
 Poiché Visual Studio definisce più di 1000 comandi, non è pratico elencarli tutti qui. Seguire invece questa procedura per individuare la definizione di un comando.

### <a name="to-locate-a-command-definition"></a>Per individuare una definizione di comando

1. In Visual Studio aprire i file seguenti nella cartella di installazione di *<Visual Studio SDK \> \VisualStudioIntegration\Common\Inc: \\* *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct* *,Menu.vsct*.

    La maggior Visual Studio comandi sono definiti in *SharedCmdDef.vsct* e *ShellCmdDef.vsct.* *VsDbgCmdUsed.vsct* definisce i comandi che riguardano il debugger *eMenumenu.vsct* definisce i comandi specifici dello sviluppo Web.

2. Se il comando è una voce di menu, prendere nota del testo esatto della voce di menu. Se il comando è un pulsante su una barra degli strumenti, prendere nota del testo della descrizione comando che viene visualizzato quando ci si sospende.

3. Premere **CTRL** + **F** per aprire la **finestra di dialogo** Trova.

4. Nella **casella Trova** digitare il testo di cui si è fatto riferimento nel passaggio 2.

5. Verificare che **Tutti i documenti** aperti sia visualizzato nella casella Cerca **in** .

6. Fare clic **sul pulsante Trova** successivo finché non viene selezionato il testo nella sezione di un elemento `<Strings>` [Button](../../extensibility/button-element.md).

    `<Button>`L'elemento in cui viene visualizzato il comando è la definizione del comando.

   Dopo aver trovato la definizione del comando, è possibile inserire una copia del comando in un altro menu o barra degli strumenti creando un [elemento CommandPlacement](../../extensibility/commandplacement-element.md) con gli stessi valori e `guid` del `id` comando. Per altre informazioni, vedere [Creare gruppi riutilizzabili di pulsanti.](../../extensibility/creating-reusable-groups-of-buttons.md)

### <a name="special-cases"></a>Casi speciali
 Nei casi seguenti, il testo del menu o della descrizione comando potrebbe non corrispondere esattamente a quanto contenuto nella definizione del comando.

- Voci di menu che includono un  carattere sottolineato, ad esempio il comando Stampa del menu **File,** in cui *la P* è sottolineata.

     I caratteri preceduti dal carattere e commerciale (&) nei nomi delle voci di menu vengono visualizzati come sottolineati. Tuttavia, i file con estensione *vsct* vengono scritti in XML, che usa il carattere e commerciale (&) per indicare caratteri speciali e richiede che una e commerciale da visualizzare sia digitata come *&amp; e*. Pertanto, in un file *con estensione vsct,* il **comando Stampa** viene visualizzato *&amp; come e. Stampare*.

- Comandi con testo dinamico, ad esempio **Salva,** e voci di menu generate dinamicamente, ad esempio \<Current Filename\> le voci **nell'elenco File** recenti.

     Non esiste un modo affidabile per eseguire ricerche nel testo dinamico. Individuare invece un gruppo che ospita il comando desiderato consultando i GUID e gli ID dei menu o dei GUID e degli ID di [Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) delle barre degli strumenti di [Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)e cercare l'ID del gruppo. Se la definizione del comando non ha il gruppo come elemento [padre,](../../extensibility/parent-element.md)cercare un elemento che imposta l'elemento padre del comando in *SharedCmdPlace.vsct* e *ShellCmdPlace.vsct* (o *VsDbgCmdPlace.vsct* per i comandi del `<CommandPlacement>` debugger). *SharedCmdPlace.vsct,* *ShellCmdPlace.vsct* e *VsDbgCmdPlace.vsct* sono nella *\<Visual Studio SDK installation path\> cartella \VisualStudioIntegration\Common\Inc. \\*

## <a name="see-also"></a>Vedi anche

- [Visual Studio file di tabella dei comandi (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Informazioni di riferimento su XML Schema VSCT](../../extensibility/vsct-xml-schema-reference.md)
