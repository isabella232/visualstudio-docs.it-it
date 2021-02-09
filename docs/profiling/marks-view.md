---
title: Visualizzazione Contrassegni | Microsoft Docs
description: Informazioni su come nella visualizzazione Contrassegni vengono visualizzati gli eventi ETW e di campionamento inseriti nell'applicazione.
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b5b7eedaf7aac4a22ca10580395e085243f831ff
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851972"
---
# <a name="marks-view"></a>Visualizzazione Contrassegni
Nella visualizzazione Contrassegni vengono mostrati gli eventi ETW e di campionamento inseriti nell'applicazione.

 I contrassegni predefiniti preinseriti nel report indicano l'inizio e la fine del programma.

 In questa visualizzazione vengono presentati anche i dati dei contatori di Windows ottenuti da contrassegni generati automaticamente. Per altre informazioni, vedere [procedura: raccogliere i dati dei contatori di Windows](../profiling/how-to-collect-windows-counter-data.md).

 Per creare un filtro tra due contrassegni, selezionare i contrassegni, fare clic con il pulsante destro del mouse sui contrassegni e quindi scegliere **Aggiungi filtro in contrassegni** o **Aggiungi filtro in timestamp**.

 Nella tabella seguente sono riportate le definizioni delle colonne disponibili nella visualizzazione Contrassegni.

 **ID contrassegno** Identificatore univoco del contrassegno di profilatura.

 **Nome contrassegno** Nome dell'evento.

 **Timestamp** Tempo compreso tra l'inizio della profilatura e il momento in cui viene registrato l'evento.

 Dati del contatore delle prestazioni di Windows Quando vengono raccolti dati del contatore delle prestazioni di Windows, i valori vengono visualizzati in una colonna che ha il nome del contatore.

## <a name="see-also"></a>Vedi anche
- [Panoramica del rapporto di prestazioni](../profiling/performance-report-overview.md)
- [Procedura: Raccogliere i dati dei contatori Windows](../profiling/how-to-collect-windows-counter-data.md)
- [&#91;&#93; finestra del controllo raccolta dati](/previous-versions/bb385767(v=vs.110))