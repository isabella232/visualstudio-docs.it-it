---
title: Serializzare le informazioni sui simboli | Microsoft Docs
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
ms.openlocfilehash: d644960153a8e342f6442f3750420ea68a61b38f
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851593"
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
