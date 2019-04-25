---
title: Visualizzazione Contrassegni | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.marks
helpviewer_keywords:
- profiling tools, Marks view
- profiling tools reports, Marks view
ms.assetid: b2773344-8081-4116-85a1-58f770448f6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: badb2266e47fcbf0bb20c5fd6fd2f7f25a167997
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830915"
---
# <a name="marks-view"></a>Visualizzazione Contrassegni
Nella visualizzazione Contrassegni vengono mostrati gli eventi ETW e di campionamento inseriti nell'applicazione.

 I contrassegni predefiniti preinseriti nel report indicano l'inizio e la fine del programma.

 In questa visualizzazione vengono presentati anche i dati dei contatori di Windows ottenuti da contrassegni generati automaticamente. Per altre informazioni, vedere [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md).

 Per creare un filtro tra due contrassegni, selezionare i contrassegni, fare clic con il pulsante destro del mouse sui contrassegni e quindi scegliere **Aggiungi filtro in contrassegni** o **Aggiungi filtro in timestamp**.

 Nella tabella seguente sono riportate le definizioni delle colonne disponibili nella visualizzazione Contrassegni.

 **ID contrassegno** Identificatore univoco del contrassegno di profilatura.

 **Nome contrassegno** Nome dell'evento.

 **Timestamp** Tempo compreso tra l'inizio della profilatura e il momento in cui viene registrato l'evento.

 Dati del contatore delle prestazioni di Windows Quando vengono raccolti dati del contatore delle prestazioni di Windows, i valori vengono visualizzati in una colonna che ha il nome del contatore.

## <a name="see-also"></a>Vedere anche
- [Panoramica del rapporto di prestazioni](../profiling/performance-report-overview.md)
- [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)
- [&#91;NIB&#93; Finestra Controllo raccolta dati](https://msdn.microsoft.com/98d740d8-459f-4605-bf04-fb17aafaaa8f)