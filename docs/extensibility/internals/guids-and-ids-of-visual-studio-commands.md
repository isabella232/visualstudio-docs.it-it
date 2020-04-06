---
title: GUID e gli ED dei comandi di Visual Studio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8932f23d301eabc97414bf76453d70336e0dabae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708258"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUID e GLI URL dei comandi di Visual Studio
I valori GUID e ID dei comandi inclusi nell'ambiente di sviluppo integrato (IDE) di Visual Studio sono definiti nei file vsct installati come parte di Visual Studio SDK. Per ulteriori informazioni, vedere [Comandi, menu e gruppi definiti dall'IDE.](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)

 Per ulteriori informazioni sull'utilizzo degli oggetti IDE definiti nei file *vsct,* vedere [Estendere menu e comandi.](../../extensibility/extending-menus-and-commands.md)

## <a name="find-a-command-definition"></a>Trovare una definizione di comandoFind a command definition
 Poiché Visual Studio definisce più di 1000 comandi, non è pratico elencarli tutti qui. Attenersi invece alla seguente procedura per individuare la definizione di un comando.

### <a name="to-locate-a-command-definition"></a>Per individuare una definizione di comando

1. In Visual Studio, aprire i file seguenti nella cartella di installazione di *<Visual Studio SDK,\>ovvero VisualStudioIntegration, Common, Inc:\\ * *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.

    La maggior parte dei comandi di Visual Studio è definita in *SharedCmdDef.vsct* e *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* definisce i comandi relativi al debugger e *Venusmenu.vsct* definisce i comandi specifici dello sviluppo Web.

2. Se il comando è una voce di menu, prendere nota del testo esatto della voce di menu. Se il comando è un pulsante di una barra degli strumenti, prendere nota del testo della descrizione comando che viene visualizzato quando si posiziona il puntatore del mouse su di esso.

3. Premere **CTRL**+**F** per aprire la finestra di dialogo **Trova.**

4. Nella casella **Trova** digitare il testo annotato nel passaggio 2.

5. Verificare che nella casella **Cerca in** sia visualizzato Tutti i **documenti aperti.**

6. Fare clic sul pulsante **Trova** successivo `<Strings>` fino a quando il testo non viene selezionato nella sezione di un [elemento Button](../../extensibility/button-element.md).

    L'elemento `<Button>` in cui viene visualizzato il comando è la definizione del comando.

   Dopo aver trovato la definizione del comando, è possibile inserire una copia del comando in `guid` `id` un altro menu o barra degli strumenti creando un [CommandPlacement elemento](../../extensibility/commandplacement-element.md) che ha gli stessi e i valori del comando. Per ulteriori informazioni, consultate [Creare gruppi riutilizzabili di pulsanti.](../../extensibility/creating-reusable-groups-of-buttons.md)

### <a name="special-cases"></a>Casi speciali
 Nei seguenti casi, il testo del menu o del testo della descrizione comando potrebbe non corrispondere esattamente a quello contenuto nella definizione del comando.

- Voci di menu che includono un carattere sottolineato, ad esempio il comando **Stampa** del menu **File,** in cui la *P* è sottolineata.

     I caratteri preceduti dal carattere e commerciale (&) nei nomi delle voci di menu vengono visualizzati come sottolineati. Tuttavia, i file *vsct* vengono scritti in XML, che utilizza il carattere e commerciale (&) per indicare caratteri speciali e richiede che una e commerciale venga digitata come * &amp;amp;*. Pertanto, in un file *vsct,* il comando **Stampa** viene visualizzato come * &amp;amp; Stampa*.

- Comandi con testo dinamico, ad\>esempio **Salva** \<nome file corrente , e voci di menu generate dinamicamente, ad esempio le voci dell'elenco File **recenti.**

     Non esiste un modo affidabile per eseguire la ricerca nel testo dinamico. Individuare invece un gruppo che ospita il comando desiderato consultando [i GUID e gli ID dei menu](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) di Visual Studio o GUID e ID delle barre degli strumenti di Visual [Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)ed eseguire una ricerca in base all'ID di tale gruppo. Se la definizione del comando non dispone del gruppo come [elemento Parent](../../extensibility/parent-element.md), cercare un elemento padre *di SharedCmdPlace.vsct* `<CommandPlacement>` e *ShellCmdPlace.vsct* (o *VsDbgCmdPlace.vsct)* per un elemento che imposta l'elemento padre del comando. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*e *VsDbgCmdPlace.vsct* si trovano nella cartella del percorso * \<\>\\ * di installazione di Visual Studio SDK.

## <a name="see-also"></a>Vedere anche

- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Riferimento allo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
