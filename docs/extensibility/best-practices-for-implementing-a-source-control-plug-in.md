---
title: Procedure consigliate per l'implementazione di un plug-in per il controllo del codice sorgente Documenti Microsoft
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
ms.openlocfilehash: 68491f22d63ae3ebb664b7c22188a661dccbf39a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740048"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Procedure consigliate per l'implementazione di un plug-in del controllo del codice sorgenteBest practices for implementing a source control plug-in
I dettagli tecnici riportati di seguito consentono di implementare in modo affidabile un plug-in del controllo del codice sorgente in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="memory-management-issues"></a>Problemi di gestione della memoria
 Nella maggior parte dei casi, l'ambiente di sviluppo integrato (IDE), ovvero il chiamante, rilascia e alloca memoria. Il plug-in del controllo del codice sorgente restituisce stringhe e altri elementi nei buffer allocati dal chiamante. Le eccezioni sono indicate nelle descrizioni di funzioni specifiche in cui si verificano.

## <a name="arrays-of-file-names"></a>Matrici di nomi di file
 Quando una matrice di file viene passata, non viene passata come matrice contigua di nomi di file. Viene passato come matrice di puntatori ai nomi di file. Ad esempio, in [SccGet](../extensibility/sccget-function.md), i nomi `lpFileNames` dei `lpFileNames` file vengono passati `char **`dal parametro , dove è in realtà un puntatore a un oggetto . `lpFileNames`[0] è un puntatore `lpFileNames`al nome, [1] è un puntatore al secondo nome e così via.

## <a name="large-model"></a>Modello grande
 Tutti i puntatori sono a 32 bit, anche su sistemi operativi a 16 bit.

## <a name="fully-qualified-paths"></a>Percorsi completi
 In cui i nomi di file o le directory vengono specificati come argomenti, devono essere percorsi completi o percorsi UNC, senza le barre rovesciate finali. È responsabilità del plug-in del controllo del codice sorgente convertire questi percorsi relativi se questo è un requisito del sistema di controllo del codice sorgente sottostante.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Specificare un percorso completo per la DLL registrata
 L'IDE non carica più le DLL da percorsi relativi (ad esempio, *.* È necessario specificare un percorso completo della DLL (ad esempio, *C:.* Questo requisito rafforza la sicurezza dell'IDE impedendo il caricamento di DLL di controllo del codice sorgente non autorizzate o rappresentate.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Verificare la presenza di un plug-in VSSCI esistente quando si installa il plug-in del controllo del codice sorgente
 Un utente che prevede di installare il plug-in del controllo del codice sorgente potrebbe già avere un plug-in del controllo del codice sorgente esistente installato nel computer. Il programma di installazione (installazione) per il plug-in creato deve determinare se sono presenti valori esistenti per le chiavi del Registro di sistema pertinenti. Se queste chiavi sono già impostate, il programma di installazione deve chiedere all'utente se registrare il plug-in come plug-in del controllo del codice sorgente predefinito e sostituire quello già installato.

## <a name="error-result-codes-and-reporting"></a>Codici dei risultati degli errori e reporting
 Il `SCC_OK` codice restituito per una funzione di controllo del codice sorgente indica che l'operazione è riuscita per tutti i file. Se l'operazione non riesce, è previsto che restituisca l'ultimo codice di errore rilevato.

 La regola per la segnalazione è che se si verifica un errore nell'IDE, l'IDE è responsabile della segnalazione. Se si verifica un errore nel sistema di controllo del codice sorgente, il plug-in del controllo del codice sorgente è responsabile della segnalazione. Ad esempio, **nessun file attualmente selezionato** verrà segnalato dall'IDE, mentre questo file è già **estratto** verrà segnalato dal plug-in.

## <a name="the-context-structure"></a>La struttura del contesto
 Durante la chiamata a [SccInitialize](../extensibility/sccinitialize-function.md), `ppvContext` il chiamante passa il parametro , che è un handle non inizializzato a un void. Il plug-in del controllo del codice sorgente può ignorare questo parametro o può allocare una struttura di qualsiasi tipo e inserire un puntatore a tale struttura nel puntatore passato. L'IDE non riconosce questa struttura, ma passa un puntatore a questa struttura in ogni altra chiamata nel plug-in. In questo modo vengono fornite informazioni preziose sulla cache di contesto al plug-in che può essere utilizzato per mantenere le informazioni sullo stato globale che vengono mantenute tra le chiamate di funzione senza l'utilizzo di variabili globali. Il plug-in è responsabile della liberazione della struttura in una chiamata a [SccUninitialize](../extensibility/sccuninitialize-function.md).

 Se il plug-in `SCC_CAP_REENTRANT` imposta il bit in [SccInitialize](../extensibility/sccinitialize-function.md) (in particolare, nel `lpSccCaps` parametro), vengono utilizzate più strutture di contesto per tenere traccia di tutti i progetti aperti.

## <a name="bitflags-and-other-command-options"></a>Flag di bit e altre opzioni di comando
 Per ogni comando, ad esempio [SccGet](../extensibility/sccget-function.md), l'IDE può specificare molte opzioni che modificano il comportamento del comando.

 L'API supporta l'impostazione di determinate `fOptions` opzioni dall'IDE tramite il parametro. Queste opzioni sono descritte in [Bitflags utilizzati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) insieme ai comandi su cui influiscono. In generale, si tratta di opzioni per le quali all'utente non verrà richiesto.

 La maggior parte delle opzioni di impostazione configurabili dall'utente non sono definite in questo modo, perché variano ampiamente tra i plug-in del controllo del codice sorgente. Pertanto, il meccanismo consigliato è un pulsante **Avanzate.** Ad esempio, nel **ottenere** finestra di dialogo, l'IDE visualizza solo le informazioni che riconosce, ma viene anche visualizzato un pulsante **Avanzate** se il plug-in dispone di opzioni per questo comando. Quando l'utente fa clic sul pulsante **Avanzate,** l'IDE chiama il [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) per abilitare il plug-in controllo del codice sorgente per richiedere all'utente informazioni, ad esempio flag di bit o una data/ora. Il plug-in restituisce queste informazioni in una `SccGet` struttura che viene passata nuovamente durante il comando.

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [Creare un plug-in del controllo del codice sorgenteCreate a source control plug-in](../extensibility/internals/creating-a-source-control-plug-in.md)
