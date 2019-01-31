---
title: 'Procedura: Salvare e modificare stringhe di connessione'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 60253ada78391c48543e81093136da15e1446f91
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55000419"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Procedura: Salvare e modificare stringhe di connessione
Le stringhe di connessione nelle applicazioni di Visual Studio vengono salvate nel file di configurazione dell'applicazione (detto anche le impostazioni dell'applicazione) o impostati come hardcoded direttamente nell'applicazione. Il salvataggio delle stringhe di connessione nel file di configurazione dell'applicazione semplifica la gestione dell'applicazione. Se la stringa di connessione richiede modifiche, infatti, è possibile aggiornarla all'interno di tale file invece di modificarla nel codice sorgente e poi ricompilare l'applicazione.

L'archiviazione di informazioni riservate, ad esempio una password, nella stringa di connessione può avere implicazioni sulla sicurezza dell'applicazione. Le stringhe di connessione salvate nel file di configurazione dell'applicazione non vengono crittografate o offuscate. Per tale motivo, chiunque può accedere al file e visualizzarne il contenuto. La sicurezza integrata di Windows consente di controllare l'accesso a un database in modo più sicuro.

Se non si sceglie di utilizzare la sicurezza integrata di Windows e il database in uso richiede l'immissione di un nome utente e di una password, è possibile ometterli nella stringa di connessione, ma sarà comunque necessario specificarli per eseguire la connessione al database. È ad esempio possibile creare una finestra di dialogo in cui vengono richieste tali informazioni e compilare la stringa di connessione dinamicamente in fase di esecuzione. Anche in questo caso possono presentarsi problemi di sicurezza se le informazioni vengono intercettate nel percorso verso il database.
Per altre informazioni, vedere [Protezione delle informazioni di connessione](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Per salvare una stringa di connessione dall'interno la configurazione guidata origine dati
Nel **configurazione guidata origine dati**, selezionare l'opzione per salvare la connessione sulle **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Per salvare una stringa di connessione direttamente nelle impostazioni dell'applicazione
1. In **Esplora soluzioni** fare doppio clic sull'icona **Progetto** (Visual Basic) o **Proprietà** (C#) per aprire **Progettazione progetti**.
1. Selezionare la scheda **Impostazioni**.
1. Nella casella **Nome** immettere un nome per la stringa di connessione. Fare riferimento a questo nome per l'accesso alla stringa di connessione nel codice.
1. Impostare **Tipo** su (**Stringa di connessione**).
1. Lasciare l'opzione **Ambito** impostata su **Applicazione**.
1. Digitare la stringa di connessione nel **valore** campo oppure fare clic il **puntini di sospensione** pulsante (...) nella **valore** campo per aprire il **"Trustmanagerconstructorarg"** finestra di dialogo per creare la stringa di connessione.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Modifica di stringhe di connessione archiviate nelle impostazioni dell'applicazione
Per modificare le informazioni sulla connessione salvate nelle impostazioni dell'applicazione, usare **Progettazione progetti**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Per modificare una stringa di connessione archiviata nelle impostazioni dell'applicazione
1. In **Esplora soluzioni** fare doppio clic sull'icona **Progetto** (Visual Basic) o **Proprietà** (C#) per aprire **Progettazione progetti**.
1. Selezionare la scheda **Impostazioni**.
1. Individuare la connessione a cui si desidera modificare e selezionare il testo nella **valore** campo.
1. Modificare la stringa di connessione nella **valore** campo oppure fare clic il **puntini di sospensione** pulsante (...) nel **valore** campo per modificare la connessione con il **connessione Proprietà** nella finestra di dialogo.

## <a name="edit-connection-strings-for-datasets"></a>Modificare le stringhe di connessione per i set di dati
È possibile modificare le informazioni di connessione per ogni oggetto TableAdapter in un set di dati.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Per modificare una stringa di connessione per un oggetto TableAdapter in un set di dati
1. Nelle **Esplora soluzioni**, fare doppio clic sul set di dati (**XSD** file) che contiene la connessione da modificare.
1. Selezionare il **TableAdapter** o query con la connessione da modificare.
1. Nel **delle proprietà** finestra, espandere il **nodo connessione**.
1. Per modificare rapidamente la stringa di connessione, modificare il **ConnectionString** proprietà, oppure fare clic sulla freccia in giù nella **connessione** proprietà e scegliere **nuova connessione**.

## <a name="security"></a>Sicurezza
L'archiviazione delle informazioni riservate, ad esempio la password, nella stringa di connessione può avere implicazioni sulla sicurezza dell'applicazione. La sicurezza integrata di Windows consente di controllare l'accesso a un database in modo più sicuro.
Per altre informazioni, vedere [Protezione delle informazioni di connessione](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Vedere anche

- [Aggiunta di connessioni](../data-tools/add-new-connections.md)