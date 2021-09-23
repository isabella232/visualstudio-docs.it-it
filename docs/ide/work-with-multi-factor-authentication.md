---
title: Usare account che richiedono l'autenticazione a più fattori
ms.date: 05/27/2020
ms.custom: SEO-VS-2020
ms.topic: conceptual
description: Informazioni su come usare Visual Studio con gli account che richiedono l'autenticazione a più fattori.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: '>=vs-2019'
ms.openlocfilehash: 2788894a98dd0433fcc191a37665dd1df0333c3e
ms.sourcegitcommit: 022ac348337f77c899996ac81060a969ebfb64bb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2021
ms.locfileid: "128133809"
---
# <a name="how-to-use-visual-studio-with-accounts-that-require-multi-factor-authentication"></a>Come usare i Visual Studio con gli account che richiedono l'autenticazione a più fattori

Quando si collabora con utenti guest esterni, è buona idea proteggere le app e i dati con criteri di accesso condizionale **(CA),** ad esempio **Multi-Factor Authentication (MFA).**  

Una volta abilitati, gli utenti guest dovranno avere più di un nome utente e una password per accedere alle risorse e dovranno soddisfare requisiti di sicurezza aggiuntivi. I criteri MFA possono essere applicati a livello di tenant, di app o di singolo utente, così come vengono abilitati per i membri dell'organizzazione. 

## <a name="how-is-the-visual-studio-experience-affected-by-mfa-policies"></a>In che modo l Visual Studio'esperienza di autenticazione a più fattori è interessata dai criteri di autenticazione a più fattori?
Le versioni di Visual Studio precedenti alla 16.6 possono avere esperienze di autenticazione ridotte se usate con account che hanno abilitato i criteri ca, ad esempio MFA, e sono associati a due o più tenant.

Questi problemi possono causare la richiesta di riautenticazione dell'istanza di Visual Studio più volte al giorno. Potrebbe essere necessario reim annotarsi le credenziali per i tenant autenticati in precedenza, anche durante lo stesso Visual Studio sessione.

## <a name="using-visual-studio-with-mfa-policies"></a>Uso Visual Studio con i criteri MFA
Nella versione 16.6 sono state aggiunte nuove funzionalità Visual Studio 2019 che semplificano il modo in cui gli utenti possono accedere alle risorse protette tramite criteri ca, ad esempio MFA. Per usare questo flusso di lavoro avanzato, è necessario acconsentire esplicitamente all'uso del Web browser predefinito del sistema come meccanismo per aggiungere e autenticare nuovamente Visual Studio account.  

> [!WARNING]
> Il non utilizzo di questo flusso di lavoro potrebbe attivare un'esperienza degradata che causa più richieste di autenticazione aggiuntive quando si aggiungono o si riautenticano Visual Studio account. 

### <a name="enabling-system-web-browser"></a>Abilitazione del Web browser di sistema

> [!NOTE] 
> Per un'esperienza ottimale, è consigliabile cancellare i dati predefiniti del Web browser del sistema prima di procedere con questo flusso di lavoro. Inoltre, se si dispone di account aziendali o dell'istituto di istruzione nel Windows 10 Impostazioni in Accedi all'istituto di istruzione o all'istituto di **istruzione,** verificare che siano autenticati correttamente.

Per abilitare questo flusso di lavoro, passare alla finestra di dialogo Opzioni di Visual Studio **(Strumenti > Opzioni...)**, selezionare la scheda **Account** e selezionare **Web browser** di sistema nell'elenco a discesa Aggiungi e riautenziona **account usando:** . 

:::image type="content" source="media/select-system-web-browser.png" alt-text="Selezionare Web browser di sistema dal menu.":::

### <a name="sign-into-additional-accounts-with-mfapolicies"></a>Accedere ad account aggiuntivi con i criteri MFA 
Dopo aver abilitato il flusso di lavoro del Web browser di sistema, è possibile accedere o aggiungere account a Visual Studio come di consueto, tramite la finestra di dialogo Account Impostazioni **(Account > file Impostazioni...)**.   
</br>
:::image type="content" source="media/add-personalization-account.png" alt-text="Aggiungere un nuovo account di personalizzazione Visual Studio." border="false":::

Questa azione aprirà il Web browser predefinito del sistema, chiederà di accedere all'account e di convalidare tutti i criteri di autenticazione a più fattori necessari.

Durante il processo di accesso, è possibile che venga visualizzata una richiesta aggiuntiva che richiede di rimanere connessi. Questa richiesta verrà visualizzata probabilmente la seconda volta che viene usato un account per l'accesso. Per ridurre al minimo la necessità di immettere di nuovo le credenziali, è consigliabile selezionare **Sì,** perché in questo modo le credenziali vengono mantenute tra le sessioni del browser.

:::image type="content" source="media/kmsi.png" alt-text="Rimanere connessi?":::

In base alle attività di sviluppo e alla configurazione delle risorse, potrebbe essere comunque richiesto di immettere nuovamente le credenziali durante la sessione. Ciò può verificarsi quando si aggiunge una nuova risorsa o si prova ad accedere a una risorsa senza aver soddisfatto in precedenza i requisiti di autorizzazione CA/MFA.

## <a name="reauthenticating-an-account"></a>Riautenticazione di un account  
Se si verifica un problema con l'account, Visual Studio potrebbe chiedere di reim microsoft le credenziali dell'account.  

:::image type="content" source="media/reauthenticate-account.png" alt-text="Autenticare nuovamente l'account Visual Studio utente.":::

Facendo clic **su Reenter your credentials (Reenter your credentials)** verrà aperto il Web browser predefinito del sistema e si tenterà di aggiornare automaticamente le credenziali. In caso di esito negativo, verrà chiesto di accedere all'account e convalidare i criteri ca/MFA necessari.

> [!NOTE] 
> Per un'esperienza ottimale, mantenere aperto il browser fino a quando non vengono convalidati tutti i criteri CA/MFA per le risorse. La chiusura del browser può comportare la perdita dello stato di autenticazione a più fattori creato in precedenza e potrebbe richiedere richieste di autorizzazione aggiuntive.

## <a name="how-to-opt-out-of-using-a-specific-azure-active-directory-tenant-in-visual-studio"></a>Come rifiutare esplicitamente l'uso di un tenant Azure Active Directory specifico in Visual Studio

Visual Studio 2019 versione 16.6 offre la flessibilità necessaria per filtrare i tenant singolarmente o globalmente, nascondendoli in modo efficace Visual Studio. Il filtro elimina la necessità di eseguire l'autenticazione con tale tenant, ma significa anche che non sarà possibile accedere alle risorse associate.

Questa funzionalità è utile quando si hanno più tenant, ma si vuole ottimizzare l'ambiente di sviluppo selezionando come destinazione un subset specifico. Può anche essere utile nei casi in cui non è possibile convalidare un criterio ca/autenticazione a più fattori specifico, in quanto è possibile filtrare il tenant che ha commesso l'errore. 

### <a name="how-to-filter-out-all-tenants"></a>Come filtrare tutti i tenant
Per filtrare a livello globale tutti i tenant, aprire la finestra di dialogo Account Impostazioni **(File > Account Impostazioni...)** e deselezionare la casella di controllo Autentica in tutte **le directory di Azure Active Directory.**

La deselezione di questa opzione garantisce l'autenticazione solo con il tenant predefinito dell'account. Significa anche che non sarà possibile accedere alle risorse associate ad altri tenant in cui l'account potrebbe essere guest.

### <a name="how-to-filter-out-individual-tenants"></a>Come filtrare singoli tenant
Per filtrare i tenant associati all'account Visual Studio, aprire la finestra di dialogo Account Impostazioni **(File > Account Impostazioni...)** e fare clic su **Applica filtro**. 
</br>
</br>

:::image type="content" source="media/apply-filter.png" alt-text="Applica filtro." border="false":::

Verrà **visualizzata la** finestra di dialogo Filtra account che consente di selezionare i tenant da usare con l'account. 

:::image type="content" source="media/select-filter-account.png" alt-text="Selezionare l'account da filtrare.":::

## <a name="see-also"></a>Vedi anche

- [Accedi a Visual Studio](signing-in-to-visual-studio.md)
- [Accesso a Visual Studio per Mac](/visualstudio/mac/signing-in)
- [Gestire più account utente](work-with-multiple-user-accounts.md)
