---
title: Usare il ciclo Read-Eval-Print Node.js
description: Visual Studio offre supporto per l'interazione con il runtime Node.js
ms.date: 12/04/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: faed930c60869010f740cf0a1e118a40299ce782
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840666"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Usare la finestra interattiva Node.js

Node.js Tools for Visual Studio include una finestra interattiva per il runtime Node.js installato. Questa finestra consente di immettere codice JavaScript e visualizzare immediatamente i risultati, nonché di eseguire comandi npm per interagire con il progetto corrente. La finestra interattiva è detta anche finestra REPL (**R**ead/**E**valuate/**P**rint **L**oop, Ciclo Read-Eval-Print).

## <a name="open-the-interactive-window"></a>Aprire la finestra interattiva

Per aprire la finestra interattiva, fare clic con il pulsante destro del mouse sul nodo del progetto Node.js in Esplora soluzioni e selezionare **Open Node.js Interactive Window** (Apri finestra interattiva Node.js).

![Finestra interattiva Node.js nel menu di scelta rapida Progetto](../javascript/media/interactivewindow-open-from-project.png)

I tasti di scelta rapida predefiniti per aprire la finestra interattiva di Node.js sono **[CTRL] + K, N**. In alternativa è possibile aprire la finestra dalla barra degli strumenti scegliendo **Visualizza** > **Finestre** > **Finestra interattiva Node.js**.

## <a name="use-the-repl"></a>Usare REPL

Dopo l'apertura della finestra è possibile immettere comandi.

![Finestra interattiva Node.js](../javascript/media/interactivewindow.png)

La finestra interattiva dispone di vari comandi predefiniti, che iniziano con un punto per distinguerli da qualsiasi funzione JavaScript dichiarata. Sono supportati i comandi seguenti:

**.cls, .clear** Cancella il contenuto della finestra dell'editor, lasciando intatti la cronologia e il contesto di esecuzione.

**.help** Visualizza la Guida per il comando specificato o per tutti i comandi e i tasti di scelta rapida se non è specificato nessun elemento.

**.info** Visualizza informazioni sull'eseguibile Node.js corrente.

**.npm** Esegue un comando npm. Se la soluzione contiene più di un progetto, specificare il progetto di destinazione usando `.npm [projectname] <npm arguments>`.

**.reset** Ripristina lo stato iniziale dell'ambiente di esecuzione, mantenendo la cronologia.

**.save** Salva la sessione REPL corrente in un file.