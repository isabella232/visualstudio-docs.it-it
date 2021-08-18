---
description: Questo messaggio indica la quantità massima di memoria virtuale che il processo ha attualmente allocato in byte (byte privati).
title: 'DA0506: numero massimo di byte privati allocati per il processo profilato | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DA0506
- vs.performance.DA0506
- vs.performance.506
ms.assetid: e9c43554-9a85-4d98-9fa4-3b19986e7b62
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5daf5ad6b727014d63e77da848a94d31b36c3c4f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142091"
---
# <a name="da0506-maximum-private-bytes-allocated-for-the-process-being-profiled"></a>DA0506: Byte privati massimi allocati per il processo sottoposto a profilatura

|Elemento|valore|
|-|-|
|ID regola|DA0506|
|Category|Monitoraggio risorse|
|Metodo di profilatura|Tutti|
|Message|Dati raccolti a solo scopo informativo. Il contatore di byte privati di processo misura la memoria virtuale allocata dal processo sottoposto a profilatura che non può essere condivisa con altri processi. Il valore restituito corrisponde al valore massimo osservato per tutti gli intervalli di misurazione.|
|Tipo regola|Informazioni|

 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.

## <a name="rule-description"></a>Descrizione della regola
 Questo messaggio indica la quantità massima di memoria virtuale che il processo ha attualmente allocato in byte (byte privati). I byte privati rappresentano percorsi di memoria virtuale allocati dal processo al quale possono accedere solo thread in esecuzione all'interno del processo.

 Per i processi a 32 bit in esecuzione in un computer a 32 bit, il limite superiore della parte privata dello spazio degli indirizzi del processo è di 2 GB. Tramite l'opzione di Boot.ini [/3 GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) i processi a 3 bit possono acquisire fino a 32 GB di memoria virtuale. Un processo a 32 bit in esecuzione su un computer a 64 bit può acquisire fino a 4 GB di memoria virtuale privata.

 Un processo a 64 bit in esecuzione su un computer a 64 bit può acquisire fino a 8 TB di memoria virtuale privata.

 Il valore indicato è il valore massimo fra tutti gli intervalli di misurazione nei quali il processo sottoposto a profilatura era attivo.

 Per altre informazioni sugli spazi degli indirizzi del processo, vedere [Virtual Address Space](/windows/win32/memory/virtual-address-space) (Spazio degli indirizzi virtuali) nella documentazione relativa alla gestione della memoria di Windows.

## <a name="how-to-use-rule-data"></a>Come usare i dati della regola
 Usare il valore indicato per confrontare le prestazioni di versioni o compilazioni diverse del programma o per ottenere informazioni sulle prestazioni dell'applicazione in scenari di profilatura diversi.

 Un valore massimo di byte privati di processo quasi al limite architettonico in base al quale vengono definite le dimensioni massime di uno spazio degli indirizzi di processo può determinare eccezioni di memoria insufficiente. Per altre informazioni, vedere [Investigating Memory Issues](/archive/msdn-magazine/2006/november/clr-inside-out-investigating-memory-issues) (Analisi dei problemi di memoria) in MSDN Magazine.
