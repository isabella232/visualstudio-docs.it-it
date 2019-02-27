---
title: 'Procedura: Serializzare le informazioni sui simboli | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 72a634bd83a55d4e646874cce5546e2a7310afb2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617847"
---
# <a name="how-to-serialize-symbol-information"></a>Procedura: Serializzare le informazioni sui simboli
È possibile serializzare i simboli necessari per analizzare l'applicazione. Con la serializzazione dei simboli vengono aggiunti simboli al file con estensione *vsp*. L'aggiunta di informazioni sui simboli nel file con estensione *vsp* consente ad altri utenti di analizzare un rapporto di prestazioni senza dover accedere ai simboli originali. Se i simboli non vengono serializzati, sarà necessario disporre dei file *exe* e *pdb* originali instrumentati per analizzare il file *vsp*.

### <a name="to-automatically-serialize-symbol-information"></a>Per serializzare automaticamente le informazioni sui simboli

1.  Scegliere **Opzioni** dal menu **Strumenti**.

     Verrà visualizzata la finestra di dialogo **Opzioni**.

2.  Fare clic su **Strumenti per le prestazioni**.

3.  In **Impostazione generale** selezionare **Serializzare automaticamente le informazioni sui simboli**.

## <a name="see-also"></a>Vedere anche
- [Configurare le sessioni di prestazioni](../profiling/configuring-performance-sessions.md)
- [Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [Procedura: Salvare file di rapporto analizzati](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))