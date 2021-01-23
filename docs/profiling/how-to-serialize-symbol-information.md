---
title: Serializzare le informazioni sui simboli | Microsoft Docs
description: Informazioni su come è possibile serializzare i simboli necessari per analizzare l'applicazione e il modo in cui la serializzazione dei simboli aggiunge simboli al file con estensione vsp.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0b7cdfa6e64380c966b62d6691f73719a3034e2d
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722087"
---
# <a name="how-to-serialize-symbol-information"></a>Procedura: Serializzare le informazioni sui simboli
È possibile serializzare i simboli necessari per analizzare l'applicazione. Con la serializzazione dei simboli vengono aggiunti simboli al file con estensione *vsp*. L'aggiunta di informazioni sui simboli nel file con estensione *vsp* consente ad altri utenti di analizzare un rapporto di prestazioni senza dover accedere ai simboli originali. Se i simboli non vengono serializzati, sarà necessario disporre dei file *exe* e *pdb* originali instrumentati per analizzare il file *vsp*.

### <a name="to-automatically-serialize-symbol-information"></a>Per serializzare automaticamente le informazioni sui simboli

1. Scegliere **Opzioni** dal menu **Strumenti**.

     Verrà visualizzata la finestra di dialogo **Opzioni**.

2. Fare clic su **Strumenti per le prestazioni**.

3. In **Impostazione generale** selezionare **Serializzare automaticamente le informazioni sui simboli**.

## <a name="see-also"></a>Vedere anche
- [Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
- [Procedura: fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [Procedura: Salvare file di rapporto analizzati](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))
