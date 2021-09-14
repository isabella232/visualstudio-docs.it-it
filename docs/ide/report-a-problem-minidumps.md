---
title: Creare minidump con tutti gli stack di chiamate
description: Informazioni su come creare minidump per un processo Visual Studio che include informazioni per tutti gli stack di chiamate.
ms.custom: SEO-VS-2020
ms.date: 06/27/2019
ms.topic: how-to
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 169401462589b12c9d0d337d442c4288bf4e16ad
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709379"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Creare minidump per un processo di Visual Studio con tutti gli stack di chiamate

In alcuni casi Microsoft potrebbe chiedere un minidump di un processo di Visual Studio in esecuzione con le informazioni per tutti gli stack di chiamate. Per raccogliere queste informazioni, seguire questa procedura:

## <a name="create-the-minidump-file"></a>Creare il file di minidump

1. Aprire una nuova istanza di Visual Studio.
1. Scegliere Debug Attach To Process **(Esegui debug** connessione a processo) dal menu  >  **principale.**
1. Selezionare le caselle di controllo **Gestito** e **Nativo** appropriate e fare clic su **Associa**.

   ![Associa a processo](../ide/media/attach-to-process.png)

1. Selezionare l'altra istanza di Visual Studio da associare nell'elenco dei processi in esecuzione.
1. Dal menu principale scegliere Debug **Interrompi**  >  **tutto.**
1. Dal menu principale scegliere **Debug**  >  **Salva dump con nome**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Ottenere gli stack di chiamate dal minidump

1. Aprire il file di dump in Visual Studio.
1. Passare a **Strumenti Opzioni** Simboli di debug e verificare che server di simboli Microsoft sia selezionato nei percorsi del file di  >    >    >   **simboli (con estensione pdb).** 
1. Aprire la finestra di **comando**(**Visualizza** > **Altre finestre** > **Finestra di comando**)
1. Digitare ‘~*k’. La finestra visualizza gli stack di chiamate di tutti i thread.
1. Copiare tutto il testo dalla finestra di comando e salvarlo in un file di testo.
1. Allegare il file txt al bug.
