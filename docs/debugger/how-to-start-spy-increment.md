---
title: 'Procedura: avviare Spy + + | Microsoft Docs'
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70874d70dd5f845e7b627f2aeb7ae51bafe45995
ms.sourcegitcommit: 7b07e7b5e06e2e13f622445c568b78a284e1a40d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2020
ms.locfileid: "76542620"
---
# <a name="how-to-start-spy"></a>Procedura: avviare Spy++

È possibile avviare Spy + + da Visual Studio o dal prompt dei comandi.

 Quando si avvia Spy + +, se viene visualizzato un messaggio per richiedere l'autorizzazione per apportare modifiche al computer, selezionare **Sì**.

> [!NOTE]
> È possibile eseguire una sola istanza di Spy + +. Se si tenta di avviare una seconda istanza, solo l'istanza attualmente in esecuzione ottiene lo stato attivo.

## <a name="prerequisites"></a>Prerequisiti

Spy + + richiede i componenti seguenti. È possibile selezionare questi componenti dal Programma di installazione di Visual Studio selezionando la scheda **singoli componenti** e quindi selezionando i componenti seguenti.

* In debug e test selezionare  **C++ strumenti per la profilatura**
* In attività di sviluppo selezionare  **C++ funzionalità di base**

Se sono state apportate modifiche, seguire le istruzioni per installare questi componenti.

## <a name="start-spy-from-visual-studio"></a>Avviare Spy + + da Visual Studio

Scegliere **Spy + +** dal menu **strumenti** .

Poiché Spy + + viene eseguito in modo indipendente, dopo averla avviata è possibile chiudere Visual Studio.

> [!NOTE]
> Quando si registrano messaggi con Spy + +, può causare un rallentamento del sistema operativo.

## <a name="start-spy-at-a-command-prompt"></a>Avviare Spy + + al prompt dei comandi

1. In una finestra del prompt dei comandi passare alla cartella che contiene spyxx. exe. In genere, il percorso di questa cartella è..\\*cartella di installazione di Visual Studio*\Common7\Tools\\.

2. Immettere **spyxx. exe**.

## <a name="see-also"></a>Vedere anche
- [Uso di Spy++](../debugger/using-spy-increment.md)
- [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)
- [riferimenti per Spy++](../debugger/spy-increment-reference.md)
