---
title: Procedure consigliate per l'utilizzo dei frammenti di codice
description: Informazioni sui frammenti di codice, sulle finalità di un frammento di codice e sul modo migliore per usarli in base all'applicazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code snippets, best practices
- code snippets, security
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 5606c09063dc72181a1011b503c745ed87c0bc47
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109643"
---
# <a name="best-practices-for-using-code-snippets"></a>Procedure consigliate per l'uso dei frammenti di codice

Il codice in un frammento illustra solo il modo più semplice per eseguire un'operazione. Per la maggior parte delle applicazioni, il codice deve essere modificato per essere adattato all'applicazione.

## <a name="handling-exceptions"></a>Gestione delle eccezioni

In genere, i blocchi Try... Catch dei frammenti di codice raccolgono e rigenerano tutte le eccezioni. Questo comportamento potrebbe anche non essere idoneo al progetto in uso. Per ogni eccezione, esistono infatti modi diversi di rispondere. Per esempi, [vedere Procedura: Gestire un'eccezione usando try/catch (C#)](/dotnet/csharp/programming-guide/exceptions/how-to-handle-an-exception-using-try-catch) e [Try... Prendere... Istruzione Finally (Visual Basic)](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement).

## <a name="file-locations"></a>Percorsi dei file

Quando i percorsi dei file vengono adattati all'applicazione, considerare quanto segue:

- Ricerca di una posizione accessibile. Gli utenti potrebbero non avere accesso alla *cartella Programmi* del computer, quindi l'archiviazione dei file con i file dell'applicazione potrebbe non funzionare.

- Ricerca di una posizione sicura. Non è sicuro archiviare i file nella cartella radice (*C:\\*). Per i dati dell'applicazione è consigliabile scegliere la cartella *Dati applicazioni*. Per i singoli dati utente, l'applicazione può creare un file per ogni utente nella cartella *Documenti*.

- Uso di un nome di file valido. È possibile usare i controlli <xref:System.Windows.Forms.OpenFileDialog> e <xref:System.Windows.Forms.SaveFileDialog> per ridurre la probabilità di nomi di file non validi. Tenere presente che tra il momento in cui l'utente seleziona un file e il momento in cui il codice lo modifica, il file potrebbe essere eliminato. Può anche succedere che l'utente non abbia le autorizzazioni per scrivere il file.

## <a name="security"></a>Sicurezza

In base a dove un frammento viene usato nel codice sorgente e a come viene modificato all'interno del codice, il livello di protezione cambia. Di seguito sono elencati alcuni aspetti da considerare.

- Accesso a file e database

- Sicurezza dall'accesso di codice

- Protezione delle risorse, ad esempio dei registri eventi e del Registro di sistema

- Archiviazione dei segreti

- Verifica degli input

- Passaggio dei dati a tecnologie script

Per altre informazioni, vedere [Protezione delle applicazioni.](../ide/securing-applications.md)

## <a name="downloaded-code-snippets"></a>Frammenti di codice scaricati

I frammenti di codice IntelliSense installati da Visual Studio non rappresentano di per sé un pericolo. Possono tuttavia mettere a rischio la sicurezza dell'applicazione. È necessario trattare i frammenti di codice scaricati da Internet con estrema cautela, come si è soliti fare per qualsiasi altro contenuto scaricato.

- È consigliabile scaricare i frammenti di codice solo da siti attendibili e usare un software antivirus aggiornato.

- Aprire tutti i file di frammenti scaricati in Blocco note o nell'editor XML di Visual Studio e analizzarli con attenzione prima di installarli. Considerare le problematiche seguenti:

  - Se eseguito, il frammento di codice potrebbe danneggiare il sistema. Leggere attentamente il codice sorgente prima di eseguirlo.

  - Il blocco URL Guida del file di frammento può contenere URL che eseguono file di script dannosi o visualizzano siti Web offensivi.

  - Il frammento di codice può contenere riferimenti che vengono automaticamente aggiunti al progetto e possono essere caricati da un punto qualsiasi nel sistema. Questi riferimenti possono essere stati scaricati nel computer dal punto in cui è stato scaricato il frammento di codice. Il frammento di codice può a questo punto chiamare un metodo nel riferimento che esegue codice dannoso. Per proteggersi da questo tipo di attacco, analizzare i blocchi delle importazioni e dei riferimenti del file di frammento.

## <a name="see-also"></a>Vedi anche

- [Visual Basic Frammenti di codice IntelliSense](/dotnet/visual-basic/developing-apps/using-ide/intellisense-code-snippets)
- [Protezione delle applicazioni](../ide/securing-applications.md)
- [Frammenti di codice](../ide/code-snippets.md)
