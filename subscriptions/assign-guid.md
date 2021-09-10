---
title: Assegnare GUID specifici a Visual Studio sottoscrittori | Microsoft Docs
author: evanwindom
ms.author: v-evwin
manager: cabuschl
ms.date: 03/19/2021
ms.topic: conceptual
description: Informazioni su come gli amministratori possono specificare il GUID della sottoscrizione per i sottoscrittori
ms.openlocfilehash: a0721029186605c6b9a277c9eb95a370a086d7d2
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123965484"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Assegnare sottoscrizioni specifiche nel portale Sottoscrizioni di Visual Studio administration

Gli amministratori possono ora usare il Sottoscrizioni di Visual Studio di amministrazione per assegnare sottoscrizioni specifiche ai singoli sottoscrittori.  Ciò può essere utile nelle situazioni in cui l'organizzazione dispone di personale temporaneo o fornitori che devono accedere a una sottoscrizione per un breve periodo di tempo.  Gli amministratori possono assegnare una sottoscrizione che è già stata usata parzialmente, lasciando le nuove sottoscrizioni per un uso a lungo termine.  

Guardare il video o leggere per informazioni su come assegnare GUID di sottoscrizioni specifiche agli utenti. 

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Assegnare GUID di sottoscrizione specifici agli utenti

Il processo di assegnazione di sottoscrizioni specifiche a singoli utenti prevede l'uso di due processi di amministrazione esistenti per assegnare a singoli utenti identificatori univoci globali (GUID) di sottoscrizione specifici.  Il processo in tre passaggi include l'esportazione di un elenco delle sottoscrizioni e delle assegnazioni correnti, l'uso di tale elenco per identificare i GUID specifici da assegnare e quindi l'uso del processo di aggiunta in blocco per caricare le nuove assegnazioni.

### <a name="export-your-subscriptions-information"></a>Esportare le informazioni sulle sottoscrizioni

Per eseguire l'esportazione:
1. Accedere al [portale di amministrazione](https://manage.visualstudio.com).
2. Selezionare la scheda **Esporta** per scaricare il file nel computer locale. Il file include il nome del contratto che contiene le sottoscrizioni utente e la data dell'esportazione.
> [!div class="mx-imgBorder"]
> ![Esportare i sottoscrittori](_img/exporting-subscriptions/exporting-subscriptions.png "Fare clic su Esporta per salvare l'elenco delle sottoscrizioni assegnate con le informazioni sul sottoscrittore.")

### <a name="identify-the-guids-you-want-to-assign"></a>Identificare i GUID da assegnare

Se in precedenza è stato usato lo strumento di esportazione, si noterà che sono stati aggiunti nuovi campi al foglio di calcolo generato.  Queste informazioni consentono di determinare lo stato di ogni sottoscrizione e quelle da assegnare agli utenti.  

- **Stato sottoscrizione:** questo campo indica "assegnato" o "non assegnato".  Se lo stato di una sottoscrizione è "assegnato", saranno associate anche informazioni utente, ad esempio nome, indirizzo di posta elettronica e così via. 
- **Stato utilizzo:** lo stato di utilizzo indicherà "nuovo", ovvero non è mai stato assegnato a un utente o "usato", che indica che è stato assegnato a un utente in un certo momento.  

È possibile usare i valori in questi campi insieme ad altre informazioni nel foglio di calcolo per determinare le sottoscrizioni da assegnare ai singoli utenti. È possibile applicare un filtro in Excel per limitare l'elenco in base allo stato, al livello di sottoscrizione, alla data di scadenza e così via. 

### <a name="upload-your-new-assignments"></a>Upload le nuove assegnazioni

Il passaggio finale consiste nel scaricare **il** modello di aggiunta in blocco, compilare le informazioni necessarie per le sottoscrizioni da assegnare e caricare il modello.  Per una descrizione completa del processo, vedere [l'articolo Aggiungere più](assign-license-bulk.md) utenti.  

> [!IMPORTANT]
> Per assicurarsi che il caricamento sia stato completato correttamente, verificare che:
> - Si sta usando il modello collegato nella finestra di dialogo quando si seleziona **Aggiungi in blocco**.  Non usare una copia archiviata in locale del modello, perché potrebbe non contenere tutti i campi obbligatori.  L'uso di un modello precedente causerà l'esito negativo del caricamento. 
> - Tutti i campi visualizzati come **Obbligatorio** nel modello sono completi.
> - Nella colonna Messaggio di errore non **sono elencati** errori.
> - Ogni GUID viene usato una sola volta nel modello. 
> - Il livello di sottoscrizione nel modello corrisponde alla sottoscrizione del GUID nell'elenco esportato. 
> - Il GUID non è già assegnato a un altro utente nell'elenco esportato. 

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="q-how-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>D: Ricerca per categorie quale sottoscrizione è attualmente assegnata a un singolo utente?
A: Se si vuole modificare il GUID assegnato a un utente, è prima necessario eliminare la sottoscrizione per tale utente.  Per altre informazioni, vedere [l'articolo Eliminare](delete-license.md) sottoscrizioni.  Dopo aver eliminato la sottoscrizione per tale utente, usare il processo descritto in precedenza per esportare l'elenco e caricare le nuove informazioni sulla sottoscrizione.  

## <a name="resources"></a>Risorse
- [Supporto delle sottoscrizioni](https://aka.ms/vsadminhelp)

## <a name="see-also"></a>Vedi anche
- [Visual Studio documentazione](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Microsoft 365 documentazione](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Ora che sono state assegnate sottoscrizioni agli utenti, scoprire come eseguire altre attività di amministrazione.
- [Assegnare sottoscrizioni singole](assign-license.md)
- [Assegnare più sottoscrizioni](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Eliminare sottoscrizioni](delete-license.md)
- [Determinare l'utilizzo massimo](maximum-usage.md)
