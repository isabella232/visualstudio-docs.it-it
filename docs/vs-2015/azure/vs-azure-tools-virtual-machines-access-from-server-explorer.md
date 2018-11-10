---
title: L'accesso a macchine virtuali di Azure da Esplora Server | Microsoft Docs
description: Ecco una panoramica su come visualizzare, creare e gestire macchine virtuali di Azure (VM) in Esplora Server in Visual Studio.
author: ghogen
manager: douge
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: e1410b3dc60ec9689b6582e794aaf10cd13092aa
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002351"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Accesso a macchine virtuali di Azure da Esplora server

Se si dispone di macchine virtuali ospitate da Azure, è possibile accedervi in Esplora Server. È prima necessario accedere alla sottoscrizione di Azure per visualizzare i servizi mobili. Per accedere, aprire il menu di scelta rapida per il nodo di Azure in Esplora Server e scegliere **Connetti a Microsoft Azure**.

1. In Cloud Explorer, scegliere una macchina virtuale e quindi premere F4 per visualizzare la finestra delle proprietà.

    Nella tabella seguente vengono illustrate le proprietà disponibili, ma sono di sola lettura. Per modificarle, usare il [portale di Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040).

   | Proprietà | Descrizione |
   | --- | --- |
   | Nome DNS |L'URL con l'indirizzo Internet della macchina virtuale. |
   | Ambiente |Per una macchina virtuale, il valore di questa proprietà è sempre produzione. |
   | nome |Il nome della macchina virtuale. |
   | Dimensione |Le dimensioni della macchina virtuale, che riflette la quantità di memoria e spazio su disco disponibile. Per altre informazioni, vedere [dimensioni delle macchine virtuali](https://docs.microsoft.com/azure/cloud-services/cloud-services-sizes-specs). |
   | Status |I valori includono avvio in corso, avviato, arresto, arrestato e recupero dello stato. Se viene visualizzato recupero dello stato, lo stato corrente è sconosciuto. I valori per questa proprietà differiscono da quelli usati nel [portale di Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040). |
   | ID sottoscrizione |L'ID sottoscrizione per l'account Azure. È possibile visualizzare queste informazioni nel [portale di Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040) visualizzando le proprietà per una sottoscrizione. |
2. Scegliere un nodo di endpoint e quindi visualizzare le **proprietà** finestra.
3. Nella tabella seguente vengono descritte le proprietà disponibili degli endpoint, ma sono di sola lettura. Per aggiungere o modificare gli endpoint per una macchina virtuale, usare il [portale di Azure](http://go.microsoft.com/fwlink/p/?LinkID=525040). 

   | Proprietà | Descrizione |
   | --- | --- |
   | nome |Un identificatore per l'endpoint. |
   | Porta privata |La porta per l'accesso alla rete interna all'applicazione. |
   | Protocollo |Il protocollo che usa il livello di trasporto per questo endpoint, TCP o UDP. |
   | Porta pubblica |La porta utilizzata per l'accesso pubblico per l'applicazione. |
