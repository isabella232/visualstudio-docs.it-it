---
title: Accesso a Macchine virtuali di Azure da Esplora server | Documentazione Microsoft
description: Panoramica su come visualizzare, creare e gestire macchine virtuali di Azure (VM) in Esplora Server in Visual Studio.
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: 653a9be556441f5f8d5fc1c1053b144dc97dd3b2
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901870"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Accesso alle macchine virtuali di Azure da Esplora server

Se ci sono macchine virtuali ospitate da Azure, è possibile accedervi in Esplora server. Per visualizzare i servizi mobili, è necessario prima di tutto accedere alla sottoscrizione Azure. Per accedere, aprire il menu di scelta rapida per il nodo Azure e scegliere **Connetti a Microsoft Azure**.

1. In Cloud Explorer scegliere una macchina virtuale e quindi premere F4 per visualizzarne la finestra delle proprietà.

    La tabella seguente illustra le proprietà disponibili, le quali sono tuttavia di sola lettura. Per modificarle, usare il [portale di Azure](https://portal.azure.com).

   | Proprietà | Descrizione |
   | --- | --- |
   | Nome DNS |URL con l'indirizzo Internet della macchina virtuale. |
   | Ambiente |Per una macchina virtuale, il valore di questa proprietà è sempre Produzione. |
   | Nome |Nome della macchina virtuale. |
   | Dimensione |Dimensioni della macchina virtuale corrispondenti alla quantità di memoria e spazio su disco disponibili. Per altre informazioni, vedere [dimensioni delle macchine virtuali](/azure/cloud-services/cloud-services-sizes-specs). |
   | Stato |I valori includono Avvio in corso, Avviato, Arresto, Arrestato e Recupero dello stato. Se viene visualizzato Recupero dello stato, lo stato corrente è sconosciuto. I valori di questa proprietà differiscono da quelli usati nel [portale di Azure](https://portal.azure.com). |
   | SubscriptionID |ID sottoscrizione dell'account Azure. È possibile vedere queste informazioni nel [portale di Azure](https://portal.azure.com) visualizzando le proprietà di una sottoscrizione. |
2. Scegliere un nodo di endpoint e quindi visualizzare la finestra **Proprietà**.
3. La tabella seguente descrive le proprietà disponibili degli endpoint, che però sono di sola lettura. Per aggiungere o modificare gli endpoint di una macchina virtuale, usare il [portale di Azure](https://portal.azure.com).

   | Proprietà | Descrizione |
   | --- | --- |
   | Nome |Identificatore dell'endpoint. |
   | Private Port |Porta per l'accesso di rete interno all'applicazione. |
   | Protocollo |Protocollo usato dal livello di trasporto per l'endpoint TCP o UDP. |
   | Public Port |Porta usata per l'accesso pubblico all'applicazione. |
