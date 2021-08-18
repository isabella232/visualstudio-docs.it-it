---
title: Implementazione di un plug-in del controllo del codice sorgente - Procedure consigliate
description: Esaminare questi dettagli tecnici per implementare in modo affidabile un plug-in di controllo del codice sorgente Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8333179533bec73379944cead37e359ecf8ae609
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051339"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Procedure consigliate per l'implementazione di un plug-in del controllo del codice sorgente
I dettagli tecnici seguenti consentono di implementare in modo affidabile un plug-in del controllo del codice sorgente in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="memory-management-issues"></a>Problemi di gestione della memoria
 Nella maggior parte dei casi, l'ambiente di sviluppo integrato (IDE), che è il chiamante, rilascia e alloca memoria. Il plug-in del controllo del codice sorgente restituisce stringhe e altri elementi nei buffer allocati dal chiamante. Le eccezioni vengono notate nelle descrizioni delle funzioni specifiche in cui si verificano.

## <a name="arrays-of-file-names"></a>Matrici di nomi di file
 Quando viene passata una matrice di file, non viene passata come matrice contigua di nomi di file. Viene passato come matrice di puntatori ai nomi di file. Ad esempio, in [SccGet](../extensibility/sccget-function.md)i nomi di file vengono passati dal parametro , dove è in realtà `lpFileNames` un `lpFileNames` puntatore a `char **` . `lpFileNames`[0] è un puntatore al nome, [1] è un puntatore `lpFileNames` al secondo nome e così via.

## <a name="large-model"></a>Modello di grandi dimensioni
 Tutti i puntatori sono a 32 bit, anche nei sistemi operativi a 16 bit.

## <a name="fully-qualified-paths"></a>Percorsi completi
 Se i nomi di file o le directory vengono specificati come argomenti, devono essere percorsi completi o PERCORSI UNC, senza le barre rovesciate finali. È responsabilità del plug-in del controllo del codice sorgente convertirlo in percorsi relativi se si tratta di un requisito del sistema di controllo del codice sorgente sottostante.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Specificare un percorso completo per la DLL registrata
 L'IDE non carica più LE DLL dai percorsi relativi (ad esempio, *.\NewProvider.dll*). È necessario specificare un percorso completo della DLL, ad esempio *C:\Providers\NewProvider.dll*. Questo requisito rafforzare la sicurezza dell'IDE impedendo il caricamento di DLL di controllo del codice sorgente non autorizzate o rappresentate.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Verificare la presenza di un plug-in VSSCI esistente quando si installa il plug-in di controllo del codice sorgente
 Un utente che prevede di installare il plug-in del controllo del codice sorgente potrebbe avere già un plug-in di controllo del codice sorgente esistente installato nel computer. Il programma di installazione (programma di installazione) per il plug-in creato deve determinare se sono presenti valori esistenti per le chiavi del Registro di sistema pertinenti. Se queste chiavi sono già impostate, il programma di installazione deve chiedere all'utente se registrare il plug-in come plug-in di controllo del codice sorgente predefinito e sostituire quello già installato.

## <a name="error-result-codes-and-reporting"></a>Codici di risultato dell'errore e creazione di report
 Il codice restituito per una funzione di controllo del codice sorgente `SCC_OK` indica che l'operazione è riuscita per tutti i file. Se l'operazione non riesce, è previsto che restituirà l'ultimo codice di errore rilevato.

 La regola per la creazione di report è che se si verifica un errore nell'IDE, l'IDE è responsabile della segnalazione. Se si verifica un errore nel sistema di controllo del codice sorgente, il plug-in del controllo del codice sorgente è responsabile della segnalazione. Ad esempio, **l'IDE** non segnala alcun file attualmente selezionato, mentre questo **file** è già estratto verrà segnalato dal plug-in.

## <a name="the-context-structure"></a>Struttura del contesto
 Durante la chiamata a [SccInitialize,](../extensibility/sccinitialize-function.md)il chiamante passa il parametro , che è un handle non `ppvContext` inizializzato a void. Il plug-in del controllo del codice sorgente può ignorare questo parametro oppure può allocare una struttura di qualsiasi tipo e inserire un puntatore a tale struttura nel puntatore passato. L'IDE non comprende questa struttura, ma passa un puntatore a questa struttura in ogni altra chiamata nel plug-in. In questo modo, al plug-in vengono fornite informazioni utili sulla cache di contesto che è possibile usare per mantenere informazioni sullo stato globali che vengono mantenute tra le chiamate di funzione senza usare variabili globali. Il plug-in è responsabile del liberare la struttura in una chiamata a [SccUninitialize.](../extensibility/sccuninitialize-function.md)

 Se il plug-in imposta il `SCC_CAP_REENTRANT` bit in [SccInitialize](../extensibility/sccinitialize-function.md) (in particolare, nel parametro ), vengono usate più strutture di contesto per tenere traccia di tutti i `lpSccCaps` progetti aperti.

## <a name="bitflags-and-other-command-options"></a>Flag di bit e altre opzioni di comando
 Per ogni comando, ad esempio [SccGet](../extensibility/sccget-function.md), l'IDE può specificare molte opzioni che modificano il comportamento del comando.

 L'API supporta l'impostazione di determinate opzioni da parte dell'IDE tramite il `fOptions` parametro . Queste opzioni sono descritte in [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) insieme ai comandi su cui influiscono. In generale, si tratta di opzioni per cui l'utente non viene richiesto.

 La maggior parte delle opzioni di impostazione configurabili dall'utente non è definita in questo modo, perché variano notevolmente tra i plug-in del controllo del codice sorgente. Pertanto, il meccanismo consigliato è **un pulsante** Avanzate. Ad esempio,  nella finestra di dialogo Ottieni l'IDE visualizza solo le  informazioni che è in grado di comprendere, ma visualizza anche un pulsante Avanzate se il plug-in dispone di opzioni per questo comando. Quando l'utente  fa clic sul pulsante Avanzate, l'IDE chiama [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) per abilitare il plug-in del controllo del codice sorgente per richiedere informazioni all'utente, ad esempio i flag di bit o una data/ora. Il plug-in restituisce queste informazioni in una struttura che viene restituita durante il `SccGet` comando.

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [Creare un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)
