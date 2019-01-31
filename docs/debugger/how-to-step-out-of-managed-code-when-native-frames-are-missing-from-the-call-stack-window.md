---
title: Passaggio di C# il codice quando sono visualizzati frame nativi mancanti dallo stack di chiamate | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 25021f0c3daffdaf59633fdb9bff0e2659f43d2e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043025"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Procedura: Uscire dal codice gestito quando nella finestra Stack di chiamate non sono visualizzati frame nativi

Se il codice contiene frame nativi non visibili nella finestra **Stack di chiamate**, l'uscita dal codice gestito può produrre risultati imprevisti. Una soluzione possibile consiste nell'utilizzare un punto di interruzione invece del comando **Esci da istruzione/routine**.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Uscire da codice gestito quando nella visualizzazione dello stack di chiamate non sono visualizzati frame nativi

1.  Nel codice nativo impostare un punto di interruzione di posizione dopo la chiamata a codice gestito.

2.  Scegliere **Continua** dal menu **Debug**.

     Una volta completata la chiamata gestita, l'esecuzione si interromperà in corrispondenza del punto di interruzione nel codice nativo.

## <a name="see-also"></a>Vedere anche

- [Procedura: Usare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md)