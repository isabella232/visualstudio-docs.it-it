---
title: Linee guida di manutenzione per le applicazioni shell isolate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 093690c293ff6857eedc50d5eccc793d7d5bb114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159278"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Linee guida per la manutenzione delle applicazioni di shell isolata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si distribuisce un'applicazione shell isolata di Visual Studio, è necessario essere in grado di fornire gli aggiornamenti software per l'applicazione dopo l'installazione. A tale scopo, è necessario installare l'applicazione utilizzando un file di Microsoft Installer (MSI). Questo tipo di installazione consente agli aggiornamenti software forniti da Microsoft di essere ridistribuiti dal Download Web e utilizzati dai clienti senza interventi personalizzati.  
  
## <a name="servicing-requirements"></a>Requisiti di manutenzione  
 È possibile assicurarsi che l'installazione della shell isolata possa consentire gli aggiornamenti assicurandosi che il programma di installazione soddisfi i tre criteri seguenti.  
  
### <a name="redistribute-by-using-an-msi"></a>Ridistribuire usando un file MSI  
 È necessario usare un'identità del servizio gestito per ridistribuire l'applicazione, perché un file MSI conserva l'identità del prodotto e verifica che l'applicazione disponga di una posizione fisica nel computer client. I moduli unione (file MSM) non forniscono tali garanzie e non devono essere utilizzate.  
  
### <a name="accounting-for-custom-actions"></a>Contabilità per le azioni personalizzate  
 Le azioni personalizzate sono direttive di installazione non standard in un programma di installazione. Le azioni personalizzate cambiano parametri, ad esempio percorsi di file, impostazioni del registro di sistema, impostazioni utente o altri elementi di installazione. Le azioni personalizzate possono modificare i dati al momento dell'installazione.  
  
 Quando si utilizzano azioni personalizzate in un programma di installazione, è necessario assicurarsi che ogni azione personalizzata della fase di installazione disponga di un'azione personalizzata corrispondente per annullare l'azione quando l'utente disinstalla l'applicazione. Se il programma di installazione non è in grado di fornire l'azione personalizzata di disinstallazione corrispondente, la rimozione dell'applicazione ne lascerà parzialmente l'installazione.  
  
- Un'azione personalizzata che si basa su una versione specifica di un file o di valori hash avrà esito negativo quando gli aggiornamenti software modificano queste versioni o valori hash. In questo caso, l'azione personalizzata deve aggiornare manualmente questi valori. Si verifica un problema aggiuntivo se le versioni di un file o di valori hash vengono condivise tra le versioni del prodotto. Evitare questa dipendenza quando possibile.  
  
### <a name="accounting-for-shared-files"></a>Contabilità per i file condivisi  
 I file condivisi hanno gli stessi nomi e vengono installati nello stesso percorso da più prodotti. Questi prodotti possono variare in base alla versione, allo SKU (Stock Keeping Unit) o a entrambi e i prodotti possono coesistere in un determinato computer. Tuttavia, i file condivisi creano problemi di manutenzione per diversi motivi:  
  
- L'aggiornamento dei file condivisi può causare problemi di compatibilità delle applicazioni perché un aggiornamento a un'applicazione può modificare la versione di un file utilizzato da una seconda applicazione che non è stata aggiornata. I programmi di installazione per i prodotti che condividono i file contano i riferimenti ai file condivisi. Pertanto, la disinstallazione di un prodotto non influisce sui file condivisi oltre il decremento del numero di istanze installate.  
  
- Il programma di installazione Quick Fix Engineering (QFE) Ripristina le versioni dei file nelle versioni dei prodotti serviti dal programma di installazione QFE. Questo processo suddivide potenzialmente un'applicazione che ha recapitato un file condiviso aggiornato.
