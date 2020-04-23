---
title: Assegnare GUID specifici ai sottoscrittori di Visual Studio . Documenti Microsoft
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/20/2020
ms.topic: conceptual
description: Informazioni su come gli amministratori possono utilizzare GUID di sottoscrizione specifici per i sottoscrittori
ms.openlocfilehash: e2e8cd4f5d07f218fc23c0b7b6f28ababc25263f
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072593"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Assegnare sottoscrizioni specifiche nel portale di amministrazione delle sottoscrizioni di Visual StudioAssign specific subscriptions in the Visual Studio Subscriptions Administration Portal

Gli amministratori possono ora utilizzare il portale di amministrazione delle sottoscrizioni di Visual Studio per assegnare sottoscrizioni specifiche ai singoli sottoscrittori.  Ciò può essere utile in situazioni in cui l'organizzazione dispone di personale temporaneo o fornitori che devono accedere a una sottoscrizione per un breve periodo.  Gli amministratori possono assegnare una sottoscrizione che è già stata parzialmente utilizzata, lasciando le nuove sottoscrizioni per un utilizzo a lungo termine.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Assegnare GUID di sottoscrizione specifici agli utentiAssign specific subscription GUIDs to users

Il processo di assegnazione di sottoscrizioni specifiche a singoli utenti prevede l'utilizzo di due processi di amministrazione esistenti per assegnare identificatori univoci globali (GUID) di sottoscrizione specifici a singoli utenti.  Il processo in tre passaggi include l'esportazione di un elenco delle sottoscrizioni e delle assegnazioni correnti, l'utilizzo di tale elenco per identificare i GUID specifici che si desidera assegnare e quindi l'utilizzo del processo di aggiunta in blocco per caricare le nuove assegnazioni.

### <a name="export-your-subscriptions-information"></a>Esportare le informazioni sulle sottoscrizioni

Per eseguire l'esportazione:
1. Accedere al [portale di amministrazione](https://manage.visualstudio.com).
2. Selezionare la scheda **Esporta** per scaricare il file nel computer locale. Il file include il nome del contratto che contiene le sottoscrizioni utente e la data dell'esportazione.
> [!div class="mx-imgBorder"]
> ![Esportare sottoscrittori](_img/exporting-subscriptions/exporting-subscriptions.png)

### <a name="identify-the-guids-you-want-to-assign"></a>Identificare i GUID che si desidera assegnare

Se in precedenza hai utilizzato lo strumento di esportazione, noterai che sono stati aggiunti nuovi campi al foglio di calcolo prodotto.  In questo modo sarà possibile determinare lo stato di ogni sottoscrizione e quelli che si desidera assegnare agli utenti.  

- **Stato sottoscrizione**: Questo campo indicherà "assegnato" o "non assegnato".  Se una sottoscrizione ha lo stato "assegnato", avrà anche informazioni utente associate, come nome, e-mail, ecc. 
- **Stato di utilizzo**: Lo stato di utilizzo indicherà "nuovo", ovvero non è mai stato assegnato a un utente o "usato" che indica che è stato assegnato a un utente a un certo punto.  

È possibile utilizzare i valori in questi campi insieme ad altre informazioni nel foglio di calcolo per determinare quali sottoscrizioni si desidera assegnare ai singoli utenti. È possibile applicare un filtro in Excel per restringere l'elenco per stato, livello di sottoscrizione, data di scadenza e così via. 

### <a name="upload-your-new-assignments"></a>Caricare i nuovi compiti

Il passaggio finale consiste nel scaricare il modello **di aggiunta in blocco,** compilare le informazioni necessarie per le sottoscrizioni che si desidera assegnare e caricare il modello.  Per una descrizione completa di tale processo, consulta il nostro articolo [Aggiungere più utenti.](assign-license-bulk.md)  

> [!IMPORTANT]
> Per garantire un caricamento riuscito, assicurati che:
> - Si utilizza il modello collegato nella finestra di dialogo quando si seleziona **Aggiunta in blocco**.  Non utilizzare una copia memorizzata localmente del modello, in quanto potrebbe non contenere tutti i campi obbligatori.  L'utilizzo di un modello precedente causerà l'esito negativo del caricamento. 
> - Tutti i campi visualizzati come **Obbligatorio** nel modello sono completi.
> - Nella colonna **Messaggio di errore** non sono presenti errori.
> - Ogni GUID viene utilizzato una sola volta nel modello. 
> - Il livello di sottoscrizione nel modello corrisponde alla sottoscrizione del GUID nell'elenco esportato. 
> - Il GUID non è già assegnato a un altro utente nell'elenco esportato. 

## <a name="frequently-asked-questions"></a>Domande frequenti
### <a name="qhow-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>D:Come si modifica la sottoscrizione attualmente assegnata a un singolo utente?
R: Se si desidera modificare il GUID assegnato a un utente, è innanzitutto necessario eliminare la sottoscrizione per tale utente.  Per ulteriori informazioni, consulta l'articolo [Eliminare abbonamenti](delete-license.md) per ulteriori informazioni.  Dopo aver eliminato la sottoscrizione per l'utente, utilizzare la procedura descritta in precedenza per esportare l'elenco e caricare le nuove informazioni sulla sottoscrizione.  

## <a name="see-also"></a>Vedere anche
- [Documentazione di Visual Studio](/visualstudio/)
- [Documentazione di Azure DevOpsAzure DevOps documentation](/azure/devops/)
- [Documentazione di Azure](/azure/)
- [Documentazione di Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Passaggi successivi
Dopo aver assegnato le sottoscrizioni agli utenti, scoprire come eseguire altre attività di amministrazione.
- [Assegnare singole sottoscrizioniAssign individual subscriptions](assign-license.md)
- [Assegnare più sottoscrizioniAssign multiple subscriptions](assign-license-bulk.md)
- [Modificare sottoscrizioni](edit-license.md)
- [Eliminare sottoscrizioni](delete-license.md)
- [Determinare l'utilizzo massimoDetermine maximum usage](maximum-usage.md)


