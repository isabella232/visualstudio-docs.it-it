---
title: Linee guida per la manutenzione di applicazioni Shell isolate | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f4139512bc63141c24b42d0ef3bd53119f4d1fb0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Le istruzioni di manutenzione per applicazioni Isolated Shell
Quando si distribuisce un'applicazione shell isolata di Visual Studio, è necessario essere in grado di fornire gli aggiornamenti software per l'applicazione dopo l'installazione. A tale scopo, è necessario installare l'applicazione utilizzando un file di Microsoft Installer (MSI). Questo tipo di installazione consente gli aggiornamenti software forniti da Microsoft per essere ridistribuito dagli Web scaricare e utilizzati dai clienti senza l'intervento personalizzato.  
  
## <a name="servicing-requirements"></a>I requisiti di manutenzione  
 È possibile assicurarsi che l'installazione di shell isolata può consentire gli aggiornamenti, assicurandosi che il programma di installazione soddisfi i seguenti criteri di tre.  
  
### <a name="redistribute-by-using-an-msi"></a>Ridistribuire utilizzando un file MSI  
 Per ridistribuire l'applicazione, è necessario utilizzare un file MSI, perché un file MSI conserva l'identità del prodotto e verificare che l'applicazione è una posizione fisica del computer client. I moduli unione (file MSM) non offrono tale garanzia e non devono essere utilizzati.  
  
### <a name="accounting-for-custom-actions"></a>Tenuto conto delle azioni personalizzate  
 Azioni personalizzate sono direttive di installazione non standard in un programma di installazione. Azioni personalizzate modificare parametri, ad esempio i percorsi dei file, impostazioni del Registro di sistema, le impostazioni utente o altri elementi di installazione. Azioni personalizzate possono modificare dati in fase di installazione.  
  
 Quando si utilizzano azioni personalizzate in un programma di installazione, è necessario assicurarsi che ogni azione personalizzata in fase di installazione deve avere un'azione personalizzata corrispondente per annullare l'operazione quando l'utente Disinstalla l'applicazione. Se i programma di installazione non riesce a fornire corrispondente Disinstalla l'azione personalizzata, rimuovere l'applicazione verrà lasciato installato parzialmente.  
  
-   Un'azione personalizzata si basa su una versione specifica di un file o hash valori avrà esito negativo durante gli aggiornamenti software modificare queste versioni o valori hash. In questo caso l'azione personalizzata è necessario aggiornare manualmente questi valori. Se le versioni di un file o hash valori vengono condivisi tra versioni del prodotto, si verifica un problema aggiuntivo. Evitare questa dipendenza, laddove possibile.  
  
### <a name="accounting-for-shared-files"></a>Tenendo conto dei file condivisi  
 File condivisi hanno gli stessi nomi e vengono installati nello stesso percorso per più prodotti. Questi prodotti possono variare in versione, Stock mantenendo Unit (SKU) o entrambi, e i prodotti possono coesistere in un computer specificato. Tuttavia, i file condivisi creano problemi di manutenzione per diversi motivi:  
  
-   Aggiornamento di file condivisi può causare problemi di compatibilità delle applicazioni perché l'aggiornamento di un'applicazione può modificare la versione di un file utilizzato da una seconda applicazione che non è stata aggiornata. Programmi di installazione per i prodotti che condividono i file di conteggio dei riferimenti ai file condivisi. Pertanto, la disinstallazione di un prodotto non influisce sul file condivisi oltre la riduzione del conteggio delle istanze installate.  
  
-   Il programma di installazione di Quick Fix Engineering (QFE) consente di ripristinare le versioni dei file per le versioni dei prodotti che ha eseguito il programma di installazione di aggiornamento rapido. Questo processo si interrompe potenzialmente un'applicazione che ha recapitato un file condiviso aggiornato.