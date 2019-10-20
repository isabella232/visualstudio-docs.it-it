---
title: Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.Build_and_Run
- VS.ToolsOptionsPag.Projects.Build_and_Run
helpviewer_keywords:
- builds [Visual Studio], setting up
- run actions
- debugger, run options
ms.assetid: c884976e-c0df-4c6d-8e3a-856ea2bd547c
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b7eb229c5938165607b797205b94a318e3303b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655182"
---
# <a name="options-dialog-box--projects-and-solutions-build-and-run"></a>Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In questa finestra di dialogo, è possibile specificare il numero massimo di progetti Visual C++ o Visual C# che è possibile compilare allo stesso tempo, determinati comportamenti di compilazione predefiniti e alcune impostazioni del log di compilazione. Per aprire la finestra di dialogo **Opzioni**, scegliere **Strumenti**, **Opzioni** nella barra dei menu. Per accedere a questo set di opzioni, espandere **Progetti e soluzioni**, quindi scegliere **Compila ed esegui**.

## <a name="uielement-list"></a>Elenco UIElement
 **numero massimo di compilazioni di progetto parallele** Specifica il numero massimo di progetti C++ visivi C# e visivi che è possibile compilare contemporaneamente. Per ottimizzare il processo di compilazione, il numero massimo di compilazioni di progetti in parallelo viene impostato automaticamente sul numero di CPU del computer. Il numero massimo è 32.

 **Compila solo i progetti di avvio e le dipendenze dall'esecuzione** Se questa casella di controllo è selezionata quando si sceglie il tasto F5, vengono compilati solo il progetto di avvio e le relative dipendenze. scegliere **debug**, **Avvia** sulla barra dei menu; in alternativa, scegliere **Compila**, **Compila** sulla barra dei menu. Se si seleziona questa casella di controllo quando si preme il tasto F5, vengono compilati tutti i progetti, le dipendenze e i file di soluzione. Scegliere **Debug**, **Avvia** oppure **Compila**, **Compila** nella barra dei menu. Per impostazione predefinita, questa opzione è deselezionata.

 **Durante l'esecuzione, quando i progetti non sono aggiornati**
 > [!NOTE]
> Questo elenco si applica solo ai progetti [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].

 Per impostazione predefinita viene visualizzato un messaggio se una configurazione del progetto non è aggiornata quando si preme il tasto F5 o si sceglie **Debug**, **Avvia** nella barra dei menu. È possibile specificare se generare comunque il progetto e se viene visualizzato il messaggio. Usare questa opzione per specificare se viene visualizzato il messaggio e quale deve essere il comportamento di compilazione se non viene visualizzato il messaggio.

 **Compila sempre** La finestra di messaggio non viene visualizzata e il progetto viene compilato nonostante la configurazione non aggiornata. Questa opzione viene impostata quando si seleziona la casella **Non visualizzare più questo messaggio**, quindi si sceglie il pulsante **Sì**.

 **Non compilare mai** La finestra di messaggio non viene visualizzata e il progetto non viene compilato. Questa opzione viene impostata quando si seleziona la casella **Non visualizzare più questo messaggio**, quindi si sceglie il pulsante **No**.

 **Richiedi compilazione** Visualizza la finestra di messaggio ogni volta che la configurazione di un progetto non è aggiornata.

 Durante l' **esecuzione, quando si verificano errori di compilazione o distribuzione** Se si verificano errori di compilazione quando si avvia una compilazione dal menu **Compila** , viene visualizzato un messaggio. È possibile specificare se continuare avviando l'applicazione e se il messaggio viene visualizzato ogni volta che si verificano errori di compilazione. Usare questa opzione per specificare se viene visualizzato il messaggio e quale deve essere il comportamento se non viene visualizzato il messaggio.

> [!NOTE]
> Questa opzione si applica solo ai progetti [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].

 **Richiedi avvio** Visualizza una finestra di messaggio ogni volta che si verificano errori di compilazione.

 **Non avviare** La finestra di messaggio non viene visualizzata e l'applicazione non viene avviata. Questa opzione viene impostata quando si seleziona la casella di controllo **Non visualizzare più questo messaggio** nella finestra di messaggio, quindi si sceglie il pulsante **No**.

 **Avvia versione precedente** La finestra di messaggio non viene visualizzata e la versione appena compilata dell'applicazione non è avviata. Questa opzione viene impostata quando si seleziona la casella di controllo **Non visualizzare più questo messaggio** nella finestra di messaggio, quindi si sceglie il pulsante **Sì**.

 **Per le nuove soluzioni, usa il progetto attualmente selezionato come progetto di avvio** Se questa casella di controllo è selezionata, le nuove soluzioni usano il progetto attualmente selezionato come progetto di avvio.

 Livello di **dettaglio output di compilazione progetto MSBuild** Determina la quantità di informazioni visualizzate nella finestra di **output** per la compilazione.

 **Livello di dettaglio file di log di compilazione progetto MSBuild**
 > [!NOTE]
> Questa opzione si applica solo ai progetti Visual C++.

 Determina la quantità di informazioni scritta nel file di log di compilazione che si trova in \\...\\*ProjectName*\Debug\\*ProjectName*.log.

## <a name="see-also"></a>Vedere anche
 [Compiling and Building](../../ide/compiling-and-building-in-visual-studio.md) (Compilazione e creazione)
