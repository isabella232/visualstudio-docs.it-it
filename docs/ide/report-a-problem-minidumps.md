---
title: Creare minidump con tutti gli stack di chiamate
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 7d0580e04968a01dc8e447a9ee35f2b1c5934ccf
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461646"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Creare minidump per un processo di Visual Studio con tutti gli stack di chiamate

In alcuni casi Microsoft potrebbe chiedere un minidump di un processo di Visual Studio in esecuzione con le informazioni per tutti gli stack di chiamate. Per raccogliere queste informazioni, seguire questa procedura:

## <a name="create-the-minidump-file"></a>Creare il file di minidump

1. Aprire una nuova istanza di Visual Studio.
1. Dal menu principale scegliere **Debug** > **Associa a processo**.
1. Selezionare le caselle di controllo **Gestito** e **Nativo** appropriate e fare clic su **Associa**.

   ![Associa a processo](../ide/media/attach-to-process.png)

1. Selezionare l'altra istanza di Visual Studio da associare nell'elenco dei processi in esecuzione.
1. Dal menu principale scegliere **Debug** > **Interrompi tutto**.
1. Dal menu principale scegliere **Debug** > **Salva dump con nome**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Ottenere gli stack di chiamate dal minidump

1. Aprire il file di dump in Visual Studio.
1. Passare a **Strumenti** > **Opzioni** > **Debug** > **Simboli** e assicurarsi che l'opzione **Server dei simboli Microsoft** sia selezionata in **Percorsi dei file di simboli (estensione pdb)** .
1. Aprire la finestra di **comando**(**Visualizza** > **Altre finestre** > **Finestra di comando**)
1. Digitare ‘~*k’. La finestra visualizza gli stack di chiamate di tutti i thread.
1. Copiare tutto il testo dalla finestra di comando e salvarlo in un file di testo.
1. Allegare il file txt al bug.
