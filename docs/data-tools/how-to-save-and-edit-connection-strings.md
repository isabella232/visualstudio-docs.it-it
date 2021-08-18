---
title: 'Procedura: salvare e modificare stringhe di connessione'
description: Informazioni su come salvare e modificare le stringhe di connessione in Visual Studio applicazioni. Salvare o modificare una stringa di connessione direttamente nelle impostazioni dell'applicazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d6ff3b07d05430ebb8ce26d4003f8ce74ab8ac4d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059281"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Procedura: Salvare e modificare stringhe di connessione
Le stringhe di connessione Visual Studio applicazioni vengono salvate nel file di configurazione dell'applicazione (definite anche impostazioni dell'applicazione) o hard coded direttamente nell'applicazione. Il salvataggio delle stringhe di connessione nel file di configurazione dell'applicazione semplifica la gestione dell'applicazione. Se la stringa di connessione richiede modifiche, infatti, è possibile aggiornarla all'interno di tale file invece di modificarla nel codice sorgente e poi ricompilare l'applicazione.

L'archiviazione di informazioni riservate, ad esempio una password, nella stringa di connessione può avere implicazioni sulla sicurezza dell'applicazione. Le stringhe di connessione salvate nel file di configurazione dell'applicazione non vengono crittografate. Per tale motivo, chiunque può accedere al file e visualizzarne il contenuto. La sicurezza integrata di Windows consente di controllare l'accesso a un database in modo più sicuro.

Se non si sceglie di utilizzare la sicurezza integrata di Windows e il database in uso richiede l'immissione di un nome utente e di una password, è possibile ometterli nella stringa di connessione, ma sarà comunque necessario specificarli per eseguire la connessione al database. È ad esempio possibile creare una finestra di dialogo in cui vengono richieste tali informazioni e compilare la stringa di connessione dinamicamente in fase di esecuzione. Anche in questo caso possono presentarsi problemi di sicurezza se le informazioni vengono intercettate nel percorso verso il database.
Per altre informazioni, vedere Protezione [delle informazioni di connessione.](/dotnet/framework/data/adonet/protecting-connection-information)

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Per salvare una stringa di connessione dalla Configurazione guidata origine dati
Nella Configurazione **guidata origine dati** selezionare l'opzione per salvare la connessione nella pagina Salva stringa di connessione nel file di configurazione **dell'applicazione** .

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Per salvare una stringa di connessione direttamente nelle impostazioni dell'applicazione
1. In **Esplora soluzioni** fare doppio clic sull'icona **Progetto** (Visual Basic) o **Proprietà** (C#) per aprire **Progettazione progetti**.
1. Selezionare la scheda **Settings** (Impostazioni).
1. Nella casella **Nome** immettere un nome per la stringa di connessione. Fare riferimento a questo nome per l'accesso alla stringa di connessione nel codice.
1. Impostare **Tipo** su (**Stringa di connessione**).
1. Lasciare l'opzione **Ambito** impostata su **Applicazione**.
1. Digitare la stringa  di connessione nel campo Valore oppure fare clic sul pulsante  con i puntini di sospensione **(...)** nel campo Valore per aprire la finestra di dialogo Proprietà connessione per compilare la stringa di connessione. 

## <a name="edit-connection-strings-stored-in-application-settings"></a>Modificare le stringhe di connessione archiviate nelle impostazioni dell'applicazione
Per modificare le informazioni sulla connessione salvate nelle impostazioni dell'applicazione, usare **Progettazione progetti**.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Per modificare una stringa di connessione archiviata nelle impostazioni dell'applicazione
1. In **Esplora soluzioni** fare doppio clic sull'icona **Progetto** (Visual Basic) o **Proprietà** (C#) per aprire **Progettazione progetti**.
1. Selezionare la scheda **Settings** (Impostazioni).
1. Individuare la connessione da modificare e selezionare il testo nel **campo** Valore.
1. Modificare la stringa  di connessione nel campo Valore oppure fare  clic sul pulsante con i puntini di sospensione **(...)** nel campo Valore per modificare la connessione con la finestra di **dialogo Proprietà** connessione .

## <a name="edit-connection-strings-for-datasets"></a>Modificare le stringhe di connessione per i set di dati
È possibile modificare le informazioni di connessione per ogni TableAdapter in un set di dati.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Per modificare una stringa di connessione per un oggetto TableAdapter in un set di dati
1. In **Esplora soluzioni** fare doppio clic sul set di dati (file **xsd)** con la connessione che si desidera modificare.
1. Selezionare **l'oggetto TableAdapter** o la query con la connessione che si desidera modificare.
1. Nella finestra **Proprietà** espandere il **nodo Connessione**.
1. Per modificare rapidamente la stringa di connessione, modificare la **proprietà ConnectionString** oppure fare clic sulla freccia rivolta verso il basso nella **proprietà Connessione** e scegliere **Nuova connessione.**

## <a name="security"></a>Sicurezza
L'archiviazione delle informazioni riservate, ad esempio la password, nella stringa di connessione può avere implicazioni sulla sicurezza dell'applicazione. La sicurezza integrata di Windows consente di controllare l'accesso a un database in modo più sicuro.
Per altre informazioni, vedere Protezione [delle informazioni di connessione.](/dotnet/framework/data/adonet/protecting-connection-information)

## <a name="see-also"></a>Vedi anche

- [Aggiunta di connessioni](../data-tools/add-new-connections.md)
