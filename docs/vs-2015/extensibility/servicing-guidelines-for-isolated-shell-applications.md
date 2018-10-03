---
title: Linee guida per la manutenzione di applicazioni Shell isolate | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dff7d9349e5081fa0e8ab64bfd32c90b83f19de3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529435"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Linee guida per la manutenzione per applicazioni della Shell isolata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [linee guida per la manutenzione per le applicazioni della Shell isolata](https://docs.microsoft.com/visualstudio/extensibility/servicing-guidelines-for-isolated-shell-applications).  
  
Quando si distribuisce un'applicazione shell isolata di Visual Studio, è necessario essere in grado di fornire gli aggiornamenti software per l'applicazione dopo l'installazione. A tale scopo, è necessario installare l'applicazione usando un file di Microsoft Installer (MSI). Questo tipo di installazione consente gli aggiornamenti software forniti da Microsoft per essere ridistribuito da Web scaricare e utilizzata dai clienti senza l'intervento personalizzato.  
  
## <a name="servicing-requirements"></a>I requisiti di manutenzione  
 È possibile garantire che l'installazione di shell isolata può consentire gli aggiornamenti, garantendo che il programma di installazione soddisfi i tre criteri seguenti.  
  
### <a name="redistribute-by-using-an-msi"></a>Ridistribuire usando un'identità del servizio gestito  
 È necessario usare un'identità del servizio gestito per ridistribuire l'applicazione, perché un file MSI mantiene l'identità del prodotto e verificare che l'applicazione è una posizione fisica del computer client. I modelli merge (file MSM) non offrono tale garanzia e non devono essere utilizzati.  
  
### <a name="accounting-for-custom-actions"></a>Tenuto conto delle azioni personalizzate  
 Azioni personalizzate sono direttive di installazione non standard in un programma di installazione. Azioni personalizzate modificano parametri, ad esempio i percorsi dei file, impostazioni del Registro di sistema, impostazioni utente o altri elementi di installazione. Azioni personalizzate potrebbero modificare i dati al momento dell'installazione.  
  
 Quando si usano azioni personalizzate in un programma di installazione, è necessario assicurarsi che ogni azione personalizzata in fase di installazione deve avere un'azione personalizzata corrispondente per annullare l'azione quando l'utente Disinstalla l'applicazione. Se i programma di installazione non riesce a fornire corrispondente Disinstalla azione personalizzata, la rimozione dell'applicazione verrà lasciato installazione parziale.  
  
-   Un'azione personalizzata che si basa su una versione specifica di un file o hash di valori avrà esito negativo quando gli aggiornamenti software modificare queste versioni o valori hash. In questo caso l'azione personalizzata è necessario aggiornare manualmente questi valori. Se le versioni di un file o hash di valori sono condivisi tra le versioni di prodotto, si verifica un problema aggiuntivo. Evitare di questa dipendenza laddove possibile.  
  
### <a name="accounting-for-shared-files"></a>Tenendo conto dei file condivisi  
 File condivisi con gli stessi nomi e vengono installati nello stesso percorso per più prodotti. Questi prodotti possono variare nella versione, Stock mantenendo Unit (SKU) o entrambi, e i prodotti possono coesistere in un determinato computer. Tuttavia, i file condivisi creano problemi di manutenzione per diversi motivi:  
  
-   L'aggiornamento di file condivisi può causare problemi di compatibilità delle applicazioni perché un aggiornamento a un'applicazione può cambiare la versione di un file utilizzato da una seconda applicazione che non è stata aggiornata. Programmi di installazione per i prodotti che condividono i file di conteggio dei riferimenti ai file condivisi. Pertanto, la disinstallazione di un prodotto non influenza i file condivisi oltre la riduzione del conteggio delle istanze installate.  
  
-   Il programma di installazione Quick Fix Engineering (QFE) consente di ripristinare le versioni dei file per le versioni dei prodotti che ha eseguito il programma di installazione QFE. Questo processo interruzioni potenzialmente di un'applicazione che ha recapitato un file condiviso aggiornato.

