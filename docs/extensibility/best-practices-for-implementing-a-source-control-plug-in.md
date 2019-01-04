---
title: Procedure consigliate per l'implementazione di un plug-in del controllo del codice sorgente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8e28733c91097094f38fa92ff0f21d54a194942
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53948407"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Procedure consigliate per implementare un plug-in del controllo del codice sorgente
I dettagli tecnici seguenti possono aiutarti a implementare in modo affidabile un plug-in controllo del codice sorgente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## <a name="memory-management-issues"></a>Problemi di gestione della memoria  
 Nella maggior parte dei casi, l'ambiente di sviluppo integrato (IDE), che è il chiamante, rilascia e alloca la memoria. Il plug-in del controllo del codice sorgente restituisce stringhe e altri elementi nei buffer allocato dal chiamante. Le eccezioni sono indicate nelle descrizioni delle funzioni specifiche in cui si verificano.  
  
## <a name="arrays-of-file-names"></a>Matrici dei nomi di file  
 Quando viene passata una matrice di file, non viene passato come matrice di nomi di file contigua. Viene passato come matrice di puntatori a nomi di file. Ad esempio, nelle [SccGet](../extensibility/sccget-function.md), i nomi dei file vengono passati per il `lpFileNames` parametro, in cui `lpFileNames` è effettivamente un puntatore a un `char **`. `lpFileNames`[0] è un puntatore al nome, `lpFileNames`[1] è un puntatore per il nome del secondo e così via.  
  
## <a name="large-model"></a>Modelli di grandi dimensioni  
 Tutti i puntatori sono a 32 bit, anche in sistemi operativi a 16 bit.  
  
## <a name="fully-qualified-paths"></a>Percorsi completi  
 In cui i nomi di file o directory vengono specificate come argomenti, devono essere percorsi completi o percorsi UNC, senza la barra rovesciata finale. È responsabilità del controllo del codice sorgente del plug-in per convertire questi valori ai percorsi relativi se vale a dire un requisito del sistema di origine sottostante.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Specificare un percorso completo per la DLL registrata  
 L'IDE non carica più DLL da percorsi relativi (ad esempio, *.\NewProvider.dll*). Specificare un percorso completo della DLL (ad esempio, *C:\Providers\NewProvider.dll*). Questo requisito rinforza la protezione dell'IDE, impedendo il caricamento del controllo del codice sorgente non autorizzati o rappresentato DLL.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Verificare la presenza di un plug-in VSSCI esistente quando si installa il plug-in del controllo del codice sorgente  
 Un utente che prevede di installare il plug-in del controllo del codice sorgente abbia già un esistente controllo del codice sorgente del plug-in installato nel computer. Il programma di installazione (installazione) per il plug-in che si crea deve determinare se sono presenti i valori esistenti per le chiavi del Registro di sistema pertinente. Se queste chiavi sono già impostate, il programma di installazione deve chiedere all'utente se si desidera registrare il plug-in come il controllo del codice sorgente predefinito plug-in e sostituita da quella che è già installato.  
  
## <a name="error-result-codes-and-reporting"></a>Codici di risultato di errore e creazione di report  
 Il `SCC_OK` restituito codice per una funzione di controllo di origine indica che l'operazione ha avuto esito positivo per tutti i file. Se l'operazione non riesce, è previsto per restituire l'ultimo codice di errore rilevato.  
  
 La regola per la segnalazione è che se si verifica un errore nell'IDE, l'IDE è responsabile che ne venga segnalato. Se si verifica un errore nel sistema di controllo di origine, il controllo del codice sorgente del plug-in è responsabile che ne venga segnalato. Ad esempio, **attualmente selezionato alcun file** sarebbe stato segnalato dall'IDE, mentre **questo file è già estratto** sarebbe stato segnalato il plug-in.  
  
## <a name="the-context-structure"></a>La struttura del contesto  
 Durante la chiamata per il [SccInitialize](../extensibility/sccinitialize-function.md), il chiamante passa il `ppvContext` parametro, ovvero un handle non inizializzato su un void. Il plug-in del controllo del codice sorgente può ignorare questo parametro oppure può allocare una struttura di qualsiasi tipo e inserire il puntatore passato un puntatore alla struttura. L'IDE non riconosce questa struttura, ma passa un puntatore a questa struttura in ogni altra chiamata nel plug-in. Fornisce informazioni della cache di contesto utile per il plug-in che può usare per gestire le informazioni di stato globale che persiste tra le chiamate di funzione senza usare le variabili globali. Il plug-in è responsabile della liberazione della struttura in una chiamata ai [SccUninitialize](../extensibility/sccuninitialize-function.md).  
  
 Se i set di plug-in di `SCC_CAP_REENTRANT` bit nel [SccInitialize](../extensibility/sccinitialize-function.md) (in particolare, nel `lpSccCaps` parametro), più strutture di contesto usate per rilevare tutti i progetti aperti.  
  
## <a name="bitflags-and-other-command-options"></a>I flag di bit e altre opzioni di comando  
 Per ogni comando, ad esempio la [SccGet](../extensibility/sccget-function.md), l'IDE può specificare numerose opzioni che modificano il comportamento del comando.  
  
 L'API supporta l'impostazione di determinate opzioni dall'IDE tramite il `fOptions` parametro. Queste opzioni sono descritte nel [flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) con i comandi che influiscono sul. In generale, queste sono le opzioni per il quale non verrebbe richiesto all'utente.  
  
 Più opzioni di impostazione configurabile dall'utente non sono definite in questo modo, perché variano notevolmente tra plug-in controllo codice sorgente. Pertanto, il metodo consigliato è un' **avanzate** pulsante. Ad esempio, nelle **ottenere** finestra di dialogo, l'IDE visualizza solo le informazioni che riconosce, ma visualizza anche un' **avanzate** pulsante se il plug-in sono disponibili opzioni per questo comando. Quando l'utente seleziona il **avanzate** pulsante, le chiamate IDE il [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) per abilitare il controllo del codice sorgente del plug-in per richiedere all'utente informazioni aggiuntive, ad esempio i flag di bit o a una data/ora. Il plug-in restituisce queste informazioni in una struttura che viene passata nuovamente durante la `SccGet` comando.  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [Creare un controllo del codice sorgente del plug-in](../extensibility/internals/creating-a-source-control-plug-in.md)