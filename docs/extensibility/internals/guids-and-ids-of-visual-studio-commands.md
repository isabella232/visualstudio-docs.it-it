---
title: GUID e ID dei comandi di Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7670eacc875bf7c5437d9bb92cc1932753093bd
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73186648"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>GUID e ID dei comandi di Visual Studio
I valori GUID e ID dei comandi inclusi in Visual Studio Integrated Development Environment (IDE) sono definiti nei file con estensione vsct installati come parte di Visual Studio SDK. Per altre informazioni, vedere [comandi, menu e gruppi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).

 Per altre informazioni su come usare gli oggetti IDE definiti nei file *vsct* , vedere [estendere i menu e i comandi](../../extensibility/extending-menus-and-commands.md).

## <a name="find-a-command-definition"></a>Trovare una definizione di comando
 Poiché Visual Studio definisce più di 1000 comandi, non è pratico elencarli tutti qui. Attenersi invece alla seguente procedura per individuare la definizione di un comando.

### <a name="to-locate-a-command-definition"></a>Per individuare una definizione di comando

1. In Visual Studio aprire i file seguenti nel percorso di *installazione di < Visual Studio SDK\>\VisualStudioIntegration\Common\Inc\\* cartella: *SharedCmdDef. vsct*, *ShellCmdDef. vsct*, *VsDbgCmdUsed. vsct*, *Venusmenu. vsct*.

    La maggior parte dei comandi di Visual Studio è definita in *SharedCmdDef. vsct* e *ShellCmdDef. vsct*. *VsDbgCmdUsed. vsct* definisce i comandi relativi al debugger e *Venusmenu. vsct* definisce i comandi specifici per lo sviluppo Web.

2. Se il comando è una voce di menu, prendere nota del testo esatto della voce di menu. Se il comando è un pulsante su una barra degli strumenti, annotare il testo della descrizione comando visualizzato quando ci si sofferma su di esso.

3. Premere **Ctrl**+**F** per aprire la finestra di dialogo **trova** .

4. Nella casella **trova** Digitare il testo annotato nel passaggio 2.

5. Verificare che **tutti i documenti aperti** siano visualizzati nella casella **Cerca in** .

6. Fare clic sul pulsante **Trova successivo** fino a quando non viene selezionato il testo nella sezione `<Strings>` di un [elemento Button](../../extensibility/button-element.md).

    L'elemento `<Button>` in cui viene visualizzato il comando è la definizione del comando.

   Una volta trovata la definizione del comando, è possibile inserire una copia del comando su un altro menu o una barra degli strumenti creando un [elemento CommandPlacement](../../extensibility/commandplacement-element.md) con lo stesso `guid` e `id` valori del comando. Per altre informazioni, vedere [creare gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md).

### <a name="special-cases"></a>Casi speciali
 Nei casi seguenti, il testo del menu o il testo della descrizione comando potrebbe non corrispondere esattamente a quello presente nella definizione del comando.

- Voci di menu che includono un carattere sottolineato, ad esempio il comando **stampa** del menu **file** , in cui il *P* è sottolineato.

     I caratteri preceduti dal carattere e commerciale (&) nei nomi delle voci di menu vengono visualizzati sotto forma di sottolineatura. Tuttavia, i file con *estensione vsct* sono scritti in XML, che usa il carattere e commerciale (&) per indicare caratteri speciali ed è necessario che una e commerciale da visualizzare sia digitata come *&amp;amp;* . Pertanto, in un file con *estensione vsct* , il comando **Print** viene visualizzato come *&amp;amp; Stampa*.

- Comandi con testo dinamico, ad esempio **Save** \<Current filename\>e le voci di menu generate dinamicamente, ad esempio gli elementi nell'elenco dei **file recenti** .

     Non esiste un modo affidabile per eseguire ricerche in testo dinamico. Trovare invece un gruppo che ospita il comando desiderato consultando [GUID e ID dei menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e ID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)e cercare l'ID del gruppo. Se la definizione del comando non dispone del gruppo come [elemento padre](../../extensibility/parent-element.md), cercare *SharedCmdPlace. vsct* e *ShellCmdPlace. vsct* (o *VsDbgCmdPlace. vsct* per i comandi del debugger) per un elemento `<CommandPlacement>` che imposta l'elemento padre del comando. *SharedCmdPlace. vsct*, *ShellCmdPlace. vsct*e *VsDbgCmdPlace. vsct* si trovano nel *percorso di installazione di\<Visual Studio SDK\>\VisualStudioIntegration\Common\Inc\\* cartella.

## <a name="see-also"></a>Vedere anche

- [File della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Riferimento XML Schema VSCT](../../extensibility/vsct-xml-schema-reference.md)
