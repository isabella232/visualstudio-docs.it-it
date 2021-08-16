---
title: Supporto di DirectX 12 in Visual Studio | Microsoft Docs
description: Gli utenti di DirectX 12 sono consigliati di usare PIX Windows per un'esperienza di debug grafico completa
ms.date: 09/29/2020
ms.topic: conceptual
author: davidcongruili
ms.author: davidli1
manager: mluparu
ms.workload:
- multiple
ms.openlocfilehash: 7a3ba160023f1bc3b3fe6c2e78ef548c4495d47bc6e102a462950223a7caa52f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121419768"
---
# <a name="directx-12-support-in-visual-studio"></a>Supporto di DirectX 12 in Visual Studio

## <a name="directx-12-support"></a>Supporto di DirectX 12

Visual Studio Diagnostica della grafica non supporta i giochi DirectX 12. Per il debug grafico con supporto completo di DirectX 12, Visual Studio consiglia *PIX in Windows*. 

PIX in Windows è uno strumento di ottimizzazione e debug delle prestazioni con funzionalità remote. PIX in Windows offre sette funzionalità principali che si adattano alle esigenze di debug grafico. Eseguire il debug e analizzare le prestazioni del rendering della grafica Direct3D 12 con acquisizioni GPU. Comprendere le prestazioni e il threading di tutte le operazioni di CPU e GPU eseguite dal gioco con acquisizioni temporali. Identificare le inefficienze nei modelli di I/O del disco del titolo e nel layout del pacchetto con le acquisizioni di I/O di file.

Premere il percorso di debug grafico con [**PIX Windows**](https://aka.ms/PIXonWindows).

[**Scaricare PIX in Windows**](https://aka.ms/downloadPIX) o [ **visualizzare la documentazione**.](https://devblogs.microsoft.com/pix/documentation/)

## <a name="pix-on-windows"></a>PIX in Windows

PIX in Windows offre sette modalità di funzionamento principali:
1. **Acquisizioni GPU per** il debug e l'analisi delle prestazioni del rendering della grafica Direct3D 12.
2. **Acquisizioni temporali** per comprendere le prestazioni e il threading di tutte le operazioni di CPU e GPU eseguite dal gioco e per tenere traccia dell'utilizzo della memoria GPU.
3. **Il riepilogo delle funzioni acquisisce** informazioni sulla durata dell'esecuzione di ogni funzione e sulla frequenza con cui ogni funzione viene chiamata.
4. **Callgraph acquisisce la** traccia dell'esecuzione di una singola funzione.
5. **Le acquisizioni di allocazione di** memoria forniscono informazioni dettagliate sulle allocazioni di memoria effettuate dal gioco.
6. **Le acquisizioni di I/O** di file consentono di identificare le inefficienze nei modelli di I/O su disco del titolo e nel layout del pacchetto.
7. **Monitor di sistema** visualizza i dati dei contatori in tempo reale durante l'esecuzione di un gioco.

Un'introduzione video dettagliata a PIX Windows è disponibile [ **qui**](https://www.youtube.com/playlist?list=PLeHvwXyqearWuPPxh6T03iwX-McPG5LkB)
