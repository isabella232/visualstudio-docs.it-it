---
title: Assegnare GUID specifici ai sottoscrittori di Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/20/2020
ms.topic: conceptual
description: Informazioni su come gli amministratori possono eseguire il GUID di sottoscrizione specifico per i sottoscrittori
ms.openlocfilehash: e6c50239721d810964f2b95e0ec3509999d2f4d5
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2020
ms.locfileid: "87235186"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Assegnare sottoscrizioni specifiche nel portale di amministrazione delle sottoscrizioni di Visual Studio

Gli amministratori possono ora utilizzare il portale di amministrazione delle sottoscrizioni di Visual Studio per assegnare sottoscrizioni specifiche ai singoli sottoscrittori.  Questo può essere utile nelle situazioni in cui l'organizzazione dispone di un personale temporaneo o di fornitori che necessitano dell'accesso a una sottoscrizione per un breve periodo di tempo.  Gli amministratori possono assegnare una sottoscrizione che è già stata usata parzialmente, lasciando le nuove sottoscrizioni per l'uso a lungo termine.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Assegnare GUID di sottoscrizione specifici agli utenti

Il processo per l'assegnazione di sottoscrizioni specifiche a singoli utenti comporta l'utilizzo di due processi di amministrazione esistenti per assegnare identificatori univoci globali (GUID) di sottoscrizione specifici a singoli utenti.  Il processo in tre passaggi include l'esportazione di un elenco delle sottoscrizioni e delle assegnazioni correnti, usando tale elenco per identificare i GUID specifici che si vuole assegnare e quindi usando il processo di aggiunta bulk per caricare le nuove assegnazioni.

### <a name="export-your-subscriptions-information"></a>Esporta le informazioni sulle sottoscrizioni

Per eseguire l'esportazione:
1. Accedere al [portale di amministrazione](https://manage.visualstudio.com).
2. Selezionare la scheda **Esporta** per scaricare il file nel computer locale. Il file include il nome del contratto che contiene le sottoscrizioni utente e la data dell'esportazione.
> [!div class="mx-imgBorder"]
> ![Esporta sottoscrittori](_img/exporting-subscriptions/exporting-subscriptions.png "Fare clic su Esporta per salvare l'elenco delle sottoscrizioni assegnate con le informazioni sul Sottoscrittore.")

### <a name="identify-the-guids-you-want-to-assign"></a>Identificare i GUID da assegnare

Se lo strumento di esportazione è stato usato in precedenza, si noterà che sono stati aggiunti nuovi campi al foglio di calcolo prodotto.  Che consentiranno di determinare lo stato di ogni sottoscrizione e quelli che si desidera assegnare agli utenti.  

- **Stato della sottoscrizione**: questo campo indicherà "assegnato" o "non assegnato".  Se a una sottoscrizione è associato lo stato "assegnato", le informazioni relative all'utente, ad esempio nome, indirizzo di posta elettronica e così via. 
- **Stato utilizzo**: lo stato di utilizzo indicherà "nuovo", ovvero non è mai stato assegnato a un utente o "utilizzato", che indica che è stato assegnato a un utente a un certo punto.  

È possibile utilizzare i valori in questi campi insieme ad altre informazioni nel foglio di calcolo per determinare quali sottoscrizioni si desidera assegnare a singoli utenti. È possibile applicare un filtro in Excel per ridurre l'elenco in base allo stato, al livello di sottoscrizione, alla data di scadenza e così via. 

### <a name="upload-your-new-assignments"></a>Caricare le nuove assegnazioni

Il passaggio finale consiste nel scaricare il modello di **aggiunta in blocco** , inserire le informazioni necessarie per le sottoscrizioni che si desidera assegnare e caricare il modello.  Per una descrizione completa del processo, vedere l'articolo [aggiungere più utenti](assign-license-bulk.md) .  

> [!IMPORTANT]
> Per assicurarsi che il caricamento venga eseguito correttamente, verificare che:
> - Si sta usando il modello collegato nella finestra di dialogo quando si seleziona **Aggiungi in blocco**.  Non usare una copia archiviata localmente del modello, perché potrebbe non contenere tutti i campi necessari.  Se si utilizza un modello obsoleto, il caricamento avrà esito negativo. 
> - Tutti i campi visualizzati come **richiesti** nel modello sono completi.
> - Nella colonna del **messaggio di errore** non sono elencati errori.
> - Ogni GUID viene usato una sola volta nel modello. 
> - Il livello di sottoscrizione nel modello corrisponde alla sottoscrizione del GUID nell'elenco esportato. 
> - Il GUID non è già assegnato a un altro utente nell'elenco esportato. 

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="qhow-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>D: modificare la sottoscrizione attualmente assegnata a un singolo utente?
R: se si desidera modificare il GUID assegnato a un utente, è innanzitutto necessario eliminare la sottoscrizione per tale utente.  Per ulteriori informazioni, vedere l'articolo [eliminare sottoscrizioni](delete-license.md) .  Dopo aver eliminato la sottoscrizione per l'utente, usare il processo descritto sopra per esportare l'elenco e caricare le nuove informazioni sulla sottoscrizione.  

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOps](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Ora che sono state assegnate sottoscrizioni agli utenti, scoprire come eseguire altre attività amministrative.
- [Assegna singole sottoscrizioni](assign-license.md)
- [Assegna più sottoscrizioni](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Eliminare sottoscrizioni](delete-license.md)
- [Determinare l'utilizzo massimo](maximum-usage.md)


