---
title: Implementazione di un plug-in del controllo del codice sorgente-procedure consigliate
description: Esaminare questi dettagli tecnici per implementare in modo affidabile un plug-in del controllo del codice sorgente in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d04b8329d425df53c5414f593393e86a3be73c47
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94974636"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Procedure consigliate per l'implementazione di un plug-in del controllo del codice sorgente
I dettagli tecnici seguenti consentono di implementare in modo affidabile un plug-in del controllo del codice sorgente in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="memory-management-issues"></a>Problemi di gestione della memoria
 Nella maggior parte dei casi, il Integrated Development Environment (IDE), ovvero il chiamante, rilascia e alloca memoria. Il plug-in del controllo del codice sorgente restituisce stringhe e altri elementi nei buffer allocati dal chiamante. Le eccezioni sono indicate nelle descrizioni di funzioni specifiche in cui si verificano.

## <a name="arrays-of-file-names"></a>Matrici di nomi file
 Quando viene passata una matrice di file, non viene passata come matrice contigua di nomi di file. Viene passato come matrice di puntatori ai nomi di file. In [SccGet](../extensibility/sccget-function.md), ad esempio, i nomi dei file vengono passati dal `lpFileNames` parametro, dove `lpFileNames` è effettivamente un puntatore a un oggetto `char **` . `lpFileNames`[0] è un puntatore al nome, `lpFileNames` [1] è un puntatore al secondo nome e così via.

## <a name="large-model"></a>Modello di grandi dimensioni
 Tutti i puntatori sono 32 bit, anche in sistemi operativi a 16 bit.

## <a name="fully-qualified-paths"></a>Percorsi completi
 Laddove i nomi di file o le directory vengono specificati come argomenti, devono essere percorsi completi o percorsi UNC, senza le barre rovesciate finali. Il plug-in del controllo del codice sorgente è responsabile della conversione di questi dati in percorsi relativi se si tratta di un requisito del sistema di controllo del codice sorgente sottostante.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Specificare un percorso completo per la DLL registrata
 L'IDE non carica più le dll dai percorsi relativi, ad esempio *.\NewProvider.dll*. È necessario specificare un percorso completo della DLL, ad esempio *C:\Providers\NewProvider.dll*. Questo requisito rafforza la sicurezza dell'IDE impedendo il caricamento di dll del controllo del codice sorgente non autorizzate o rappresentate.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Verificare la presenza di un plug-in VSSCI esistente quando si installa il plug-in del controllo del codice sorgente
 Un utente che prevede di installare il plug-in del controllo del codice sorgente potrebbe avere già installato un plug-in del controllo del codice sorgente esistente nel computer. Il programma di installazione (installazione) per il plug-in creato deve determinare se sono presenti valori esistenti per le chiavi del registro di sistema pertinenti. Se queste chiavi sono già impostate, il programma di installazione deve richiedere all'utente se registrare il plug-in come plug-in del controllo del codice sorgente predefinito e sostituire quello già installato.

## <a name="error-result-codes-and-reporting"></a>Codici di risultato dell'errore e creazione di report
 Il `SCC_OK` codice restituito per una funzione di controllo del codice sorgente indica che l'operazione ha avuto esito positivo per tutti i file. Se l'operazione ha esito negativo, si prevede che venga restituito l'ultimo codice di errore rilevato.

 La regola per la creazione di report è che se si verifica un errore nell'IDE, l'IDE è responsabile della creazione di report. Se si verifica un errore nel sistema di controllo del codice sorgente, il plug-in del controllo del codice sorgente è responsabile della creazione di report. Ad esempio, **Nessun file attualmente selezionato** verrebbe segnalato dall'IDE, mentre **questo file è già estratto** verrebbe segnalato dal plug-in.

## <a name="the-context-structure"></a>Struttura del contesto
 Durante la chiamata a [SccInitialize](../extensibility/sccinitialize-function.md), il chiamante passa il `ppvContext` parametro, che è un handle non inizializzato a un void. Il plug-in del controllo del codice sorgente può ignorare questo parametro oppure può allocare una struttura di qualsiasi tipo e inserire un puntatore a tale struttura nel puntatore passato. L'IDE non comprende questa struttura, ma passa un puntatore a questa struttura in tutte le altre chiamate nel plug-in. In questo modo vengono fornite informazioni utili sulla cache del contesto per il plug-in che è possibile utilizzare per mantenere le informazioni sullo stato globale che vengono mantenute tra le chiamate di funzione senza utilizzare variabili globali. Il plug-in è responsabile della liberazione della struttura in una chiamata a [SccUninitialize](../extensibility/sccuninitialize-function.md).

 Se il plug-in imposta il `SCC_CAP_REENTRANT` bit in [SccInitialize](../extensibility/sccinitialize-function.md) (in particolare, nel `lpSccCaps` parametro), vengono utilizzate più strutture di contesto per tenere traccia di tutti i progetti aperti.

## <a name="bitflags-and-other-command-options"></a>Flag e altre opzioni di comando
 Per ogni comando, ad esempio [SccGet](../extensibility/sccget-function.md), l'IDE può specificare molte opzioni che modificano il comportamento del comando.

 L'API supporta l'impostazione di determinate opzioni da parte dell'IDE tramite il `fOptions` parametro. Queste opzioni sono descritte in [flag usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) insieme ai comandi che influiscono su di essi. In generale, si tratta di opzioni per le quali l'utente non viene richiesto.

 La maggior parte delle opzioni di impostazione configurabili dall'utente non sono definite in questo modo, in quanto variano notevolmente tra i plug-in del controllo del codice sorgente. Pertanto, il meccanismo consigliato è un pulsante **Avanzate** . Nella finestra di dialogo **Ottieni** , ad esempio, l'IDE Visualizza solo le informazioni che riconosce, ma Visualizza anche un pulsante **Avanzate** se il plug-in include opzioni per questo comando. Quando l'utente fa clic sul pulsante **Avanzate** , l'IDE chiama [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) per abilitare il plug-in del controllo del codice sorgente per richiedere informazioni all'utente, ad esempio flag o una data/ora. Il plug-in restituisce queste informazioni in una struttura che viene passata di nuovo durante il `SccGet` comando.

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)
