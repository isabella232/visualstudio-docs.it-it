---
title: Avviare spy++ | Microsoft Docs
description: Informazioni su come avviare lo strumento Spy++ da un Visual Studio o da un prompt dei comandi quando si vuole eseguire il debug di una soluzione.
ms.custom: SEO-VS-2020
ms.date: 12/16/2018
ms.topic: how-to
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b295246db8429689d0eedad7616ccff2f7c0010dd18c08a78a642a5abf886531
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121378749"
---
# <a name="how-to-start-spy"></a>Procedura: avviare Spy++

È possibile avviare Spy++ da un Visual Studio o da un prompt dei comandi.

 Quando si avvia Spy++, se viene visualizzato un messaggio per chiedere l'autorizzazione per apportare modifiche al computer, selezionare **Sì**.

> [!NOTE]
> È possibile eseguire una sola istanza di Spy++. Se si tenta di avviare una seconda istanza, l'istanza attualmente in esecuzione ottiene lo stato attivo.

## <a name="prerequisites"></a>Prerequisiti

Spy++ richiede i componenti seguenti. È possibile selezionare questi componenti dal Programma di installazione di Visual Studio selezionando la **scheda Singoli** componenti e quindi selezionando i componenti seguenti.

* In Debug e test selezionare **Strumenti di profilatura C++**
* In Attività di sviluppo selezionare **Funzionalità principali C++**

Se sono state apportate modifiche, seguire le istruzioni per installare questi componenti.

## <a name="start-spy-from-visual-studio"></a>Avviare Spy++ da Visual Studio

Scegliere  **Spy++ dal** menu Strumenti .

Poiché Spy++ viene eseguito in modo indipendente, dopo l'avvio è possibile chiudere Visual Studio.

> [!NOTE]
> Quando si registrano messaggi con Spy++, le prestazioni del sistema operativo potrebbero risultare più lente.

## <a name="start-spy-at-a-command-prompt"></a>Avviare Spy++ al prompt dei comandi

1. In una finestra del prompt dei comandi passare alla cartella che contiene spyxx.exe. In genere, il percorso di questa cartella è . \\ *Visual Studio cartella di installazione*\Common7\Tools \\ .

2. Immettere **spyxx.exe**.

## <a name="see-also"></a>Vedi anche
- [Utilizzo di Spy++](../debugger/using-spy-increment.md)
- [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)
- [Riferimenti per Spy++](../debugger/spy-increment-reference.md)
