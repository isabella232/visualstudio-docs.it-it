---
title: Procedure consigliate per l'uso dei frammenti di codice | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
ms.assetid: a293ec17-4dd7-4a99-8eeb-99f44a822a8b
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1dad7bd7ccddf3645abb11dc55afcdf2e7cce7ad
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49919910"
---
# <a name="best-practices-for-using-code-snippets"></a>Procedure consigliate per l'utilizzo dei frammenti di codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il codice in un frammento illustra solo il modo più semplice per eseguire un'operazione. Per la maggior parte delle applicazioni, il codice deve essere modificato per essere adattato all'applicazione.  
  
## <a name="handling-exceptions"></a>Gestione delle eccezioni  
 In genere, i blocchi Try... Catch dei frammenti di codice raccolgono e rigenerano tutte le eccezioni. Questo comportamento potrebbe anche non essere idoneo al progetto in uso. Per ogni eccezione, esistono infatti modi diversi di rispondere. Vedere ad esempio [Procedura: Gestire un'eccezione usando Try/Catch (Guida per programmatori C#)](http://msdn.microsoft.com/library/ca8e3773-980e-4767-8633-7408540e9818) e [Try...Catch...Finally Statement](http://msdn.microsoft.com/library/d6488026-ccb3-42b8-a810-0d97b9d6472b) (Istruzione Try...Catch...Finally).  
  
## <a name="file-locations"></a>Percorsi dei file  
 Quando i percorsi dei file vengono adattati all'applicazione, considerare quanto segue:  
  
-   Ricerca di una posizione accessibile. È possibile che gli utenti non accedano alla cartella Programmi del computer. Archiviare i file insieme ai file dell'applicazione potrebbe non essere la scelta corretta.  
  
-   Ricerca di una posizione sicura. Non è sicuro archiviare i il file nella cartella radice (C:\\). Per i dati dell'applicazione, è consigliabile scegliere la cartella \Dati applicazioni. Per i singoli dati utente, l'applicazione può creare un file per ogni utente nella cartella Documenti.  
  
-   Uso di un nome di file valido. È possibile usare i controlli <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> per ridurre la probabilità di nomi di file non validi. Tenere presente che tra il momento in cui l'utente seleziona un file e il momento in cui il codice lo modifica, il file potrebbe essere eliminato. Può anche succedere che l'utente non abbia le autorizzazioni per scrivere il file.  
  
## <a name="security"></a>Sicurezza  
 In base a dove un frammento viene usato nel codice sorgente e a come viene modificato all'interno del codice, il livello di protezione cambia. Di seguito sono elencati alcuni aspetti da considerare.  
  
- Accesso a file e database  
  
- Sicurezza dall'accesso di codice  
  
- Protezione delle risorse, ad esempio dei registri eventi e del Registro di sistema  
  
- Archiviazione dei segreti  
  
- Verifica degli input  
  
- Passaggio dei dati a tecnologie script  
  
  Per altre informazioni, vedere [Securing Applications](../ide/securing-applications.md) (Protezione delle applicazioni).  
  
## <a name="downloaded-code-snippets"></a>Frammenti di codice scaricati  
 I frammenti di codice IntelliSense installati da Visual Studio non rappresentano di per sé un pericolo. Possono tuttavia mettere a rischio la sicurezza dell'applicazione. È necessario trattare i frammenti di codice scaricati da Internet con estrema cautela, come si è soliti fare per qualsiasi altro contenuto scaricato.  
  
-   È consigliabile scaricare i frammenti di codice solo da siti attendibili e usare un software antivirus aggiornato.  
  
-   Aprire tutti i file di frammenti scaricati in Blocco note o nell'editor XML di Visual Studio e analizzarli con attenzione prima di installarli. Considerare le problematiche seguenti:  
  
    -   Se eseguito, il frammento di codice potrebbe danneggiare il sistema. Leggere attentamente il codice sorgente prima di eseguirlo.  
  
    -   Il blocco URL Guida del file di frammento può contenere URL che eseguono file di script dannosi o visualizzano un sito Web offensivo.  
  
    -   Il frammento di codice può contenere riferimenti che vengono automaticamente aggiunti al progetto e possono essere caricati da un punto qualsiasi nel sistema. Questi riferimenti possono essere stati scaricati nel computer dal punto in cui è stato scaricato il frammento di codice. Il frammento di codice può a questo punto chiamare un metodo nel riferimento che esegue codice dannoso. Per proteggersi da questo tipo di attacco, analizzare i blocchi delle importazioni e dei riferimenti del file di frammento.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Basic IntelliSense Code Snippets](http://msdn.microsoft.com/library/ffdde4c9-8141-4906-b09b-15181357a643)  (Frammenti di codice IntelliSense di Visual Basic)  
 [Securing Applications](../ide/securing-applications.md)  (Protezione delle applicazioni)  
 [Frammenti di codice](../ide/code-snippets.md)



