---
title: Creare minidump con tutti gli stack di chiamate
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 7b3be91e5d0d2e1f14724dd647670fc4885bcd4d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "77271195"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Creare minidump per un processo di Visual Studio con tutti gli stack di chiamate

In alcuni casi Microsoft potrebbe chiedere un minidump di un processo di Visual Studio in esecuzione con le informazioni per tutti gli stack di chiamate. Per raccogliere queste informazioni, seguire questa procedura:

## <a name="create-the-minidump-file"></a>Creare il file di minidump

1. Aprire una nuova istanza di Visual Studio.
1. Dal menu principale, scegliere **Esegui debug** > **collega al processo**.
1. Selezionare le caselle di controllo **Gestito** e **Nativo** appropriate e fare clic su **Associa**.

   ![Associa a processo](../ide/media/attach-to-process.png)

1. Selezionare l'altra istanza di Visual Studio da associare nell'elenco dei processi in esecuzione.
1. Dal menu principale, scegliere **Interruzione di debug** > **tutto**.
1. Dal menu principale, scegliere **Debug** > **dump salvataggio con nome**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Ottenere gli stack di chiamate dal minidump

1. Aprire il file di dump in Visual Studio.
1. Passare a **Opzioni di strumenti** > **i** > **simboli** di**debug** > e assicurarsi che **Microsoft Symbol Servers** sia selezionato nel percorso del file di simboli **(con estensione pdb).**
1. Aprire la finestra di **comando**(**Visualizza** > **Altre finestre** > **Finestra di comando**)
1. Digitare ‘~*k’. La finestra visualizza gli stack di chiamate di tutti i thread.
1. Copiare tutto il testo dalla finestra di comando e salvarlo in un file di testo.
1. Allegare il file txt al bug.
