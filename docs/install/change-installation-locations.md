---
title: Cambiare i percorsi di installazione in Visual Studio 2017
description: Informazioni su come ridurre il footprint di installazione sull'unità del sistema modificando il percorso della Download Cache, dei componenti condivisi, degli SDK e degli strumenti in unità diverse.
ms.date: 05/07/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- change installation locations for Visual Studio
- move installation files to different drives
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 887ebca8645ab30d6d284433baf58451ab10b80c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49869379"
---
# <a name="change-the-installation-locations-in-visual-studio-2017"></a>Cambiare i percorsi di installazione in Visual Studio 2017

**Novità nella versione 15.7**: è possibile ridurre il footprint di installazione sull'unità del sistema spostando la Download Cache, i componenti condivisi, gli SDK e gli strumenti in unità diverse.

Ecco come fare.

1. Quando si installa Visual Studio scegliere la scheda **Opzioni di installazione**.

   ![Visual Studio 2017 - Modificare il percorso di installazione](media/installation-options-by-location.png "Modificare il percorso di installazione")

   > [!IMPORTANT]
   > Se si sospende e successivamente si riavvia l'installazione, Visual Studio riprende dal punto in cui è stato interrotto. In altre parole, lo stato dell'installazione si riferisce ai dati ancora da scaricare e installare e non inizia dal conteggio precedente.

2. Nella sezione **IDE di Visual Studio** accettare il valore predefinito. In questo modo viene installato il prodotto principale e vengono inclusi file specifici per questa versione di Visual Studio.

   > [!IMPORTANT]
   > Se l'unità di sistema è un'unità SSD, si consiglia di accettare il percorso predefinito nell'unità di sistema: quando si sviluppa in Visual Studio, si legge e si scrive da e in una grande quantità di file, aumentando l'attività di I/O del disco.  È opportuno scegliere l'unità più veloce per gestire il carico.

3. Nella sezione **Download Cache** decidere se si vuole mantenere la Download Cache e quindi selezionare o deselezionare l'opzione **Mantieni la Download Cache**. <br><br>Se si decide di non mantenere la Download Cache, il percorso viene usato solo temporaneamente. Inoltre, questa azione non influisce sui file di installazioni precedenti né li elimina. Per pulire tutti i pacchetti di installazione, è necessario modificare separatamente le installazioni precedenti.

4. Nella sezione **Download Cache** specificare l'unità in cui verranno archiviati i file di installazione e i manifesti. <br><br>Ad esempio, se si seleziona il carico di lavoro "Sviluppo di applicazioni desktop con C++", le dimensioni richieste temporaneamente sono 1,58 GB nell'unità di sistema, spazio che verrà liberato non appena viene completata l'installazione.

   > [!NOTE]
   > I file vengono prima scaricati in una cartella temporanea nell'unità di sistema e successivamente eliminati dopo che Visual Studio li verifica e li sposta nella cartella della Download Cache. Se si sceglie di mantenere la Download Cache in un'unità diversa, Visual Studio richiede comunque uno spazio su disco equivalente alle dimensioni della Download Cache nell'unità di sistema.
   > [!IMPORTANT]
   > Il percorso viene impostato con la prima installazione e non può essere modificato in un secondo tempo dall'interfaccia utente del programma di installazione. Si dovranno invece [usare i parametri della riga di comando](use-command-line-parameters-to-install-visual-studio.md) per spostare la Download Cache

5. Nella sezione **Componenti condivisi, strumenti e SDK** specificare l'unità in cui si vogliono archiviare i file condivisi dalle installazioni side-by-side di Visual Studio. Anche gli SDK e gli strumenti che consentono al programma di installazione di Visual Studio di cambiare il proprio percorso di installazione sono archiviati in questa directory.

   > [!NOTE]
   > Esistono alcuni strumenti e SDK con regole diverse riguardo al percorso in cui possono essere installati. Questi strumenti e SDK verranno comunque installati nell'unità di sistema anche se si sceglie un altro percorso.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installare Visual Studio 2017](install-visual-studio.md)
* [Aggiornare Visual Studio 2017](update-visual-studio.md)
* [Modificare Visual Studio 2017](update-visual-studio.md)
* [Disinstallare Visual Studio 2017](uninstall-visual-studio.md)
