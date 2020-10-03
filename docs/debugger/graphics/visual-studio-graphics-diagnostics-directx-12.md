---
title: Supporto di DirectX 12 in Visual Studio | Microsoft Docs
description: Si consiglia agli utenti di DirectX 12 di usare PIX in Windows per un'esperienza di debug grafico completa
ms.date: 09/29/2020
ms.topic: conceptual
author: davidcongruili
ms.author: davidli1
manager: mluparu
ms.workload:
- multiple
ms.openlocfilehash: 9dbc52a0233abe467da4d41af0134663bc7cd9df
ms.sourcegitcommit: a1cb4e2025045c2ad79167645c4c0f33b94b1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671397"
---
# <a name="directx-12-support-in-visual-studio"></a>Supporto di DirectX 12 in Visual Studio

## <a name="directx-12-support"></a>Supporto per DirectX 12

Visual Studio Diagnostica della grafica non supporta i giochi DirectX 12. Per il debug grafico con supporto completo di DirectX 12, Visual Studio consiglia *pix per Windows*. 

PIX in Windows è uno strumento di ottimizzazione e debug delle prestazioni con funzionalità remote. PIX in Windows offre sette funzionalità principali che soddisfano le esigenze di debug grafico. Eseguire il debug e analizzare le prestazioni del rendering di grafica Direct3D 12 con le acquisizioni GPU. Informazioni sulle prestazioni e il threading di tutte le operazioni di CPU e GPU eseguite dal gioco con acquisizioni di temporizzazione. Identificare le inefficienze nei modelli di i/o del disco del titolo e nel layout dei pacchetti con acquisizioni di i/o di file.

Premere il percorso di debug grafico con [**pix in Windows**](https://aka.ms/PIXonWindows).

[**Scaricare pix in Windows**](https://aka.ms/downloadPIX) o [ **visualizzare la documentazione**.](https://devblogs.microsoft.com/pix/documentation/)

## <a name="pix-on-windows"></a>PIX in Windows

PIX in Windows presenta sette modalità operative principali:
1. **Acquisizione GPU** per il debug e l'analisi delle prestazioni del rendering della grafica Direct3D 12.
2. **Temporizzazione acquisisce** per comprendere le prestazioni e il threading di tutte le operazioni di CPU e GPU eseguite dal gioco e per tenere traccia dell'utilizzo della memoria GPU.
3. Le **acquisizioni di riepilogo delle funzioni** accumulano informazioni sul tempo di esecuzione di ogni funzione e sulla frequenza con cui ogni funzione viene chiamata.
4. **Grafico chiamate acquisisce** traccia dell'esecuzione di una singola funzione.
5. Le **acquisizioni di allocazione di memoria** forniscono informazioni approfondite sulle allocazioni di memoria effettuate dal gioco.
6. Le acquisizioni di i/o di **file** consentono di identificare le inefficienze nei modelli di i/o del disco del titolo e nel layout del pacchetto.
7. **Monitoraggio di sistema** consente di visualizzare i dati dei contatori in tempo reale durante l'esecuzione di un gioco.

Un video dettagliato introduttivo a PIX in Windows è disponibile [ **qui**](https://www.youtube.com/playlist?list=PLeHvwXyqearWuPPxh6T03iwX-McPG5LkB)
