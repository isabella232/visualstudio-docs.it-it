---
description: Nell'esempio Dia2dump viene illustrato come utilizzare Microsoft Debug Interface Access Software Development Kit (DIA SDK) per eseguire una query su un file PDB per ottenere informazioni.
title: Esempio Dia2dump | Microsoft Docs
ms.date: 07/24/2018
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a94a16d8e9fd60b042ea7113304b6d14c649b6fa
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149186"
---
# <a name="dia2dump-sample"></a>Esempio Dia2dump

Nell'esempio Dia2dump viene illustrato come utilizzare Microsoft Debug Interface Access Software Development Kit (DIA SDK) per eseguire una query su un file PDB per ottenere informazioni.

L'esempio Dia2dump viene installato con Visual Studio e contiene i file di soluzione e di origine. L'eseguibile compilato viene eseguito dalla riga di comando. Può visualizzare il contenuto di un intero file di database di programma (con estensione pdb) o solo le sezioni a cui si è interessati.

## <a name="install-the-sample"></a>Installare l'esempio

L'esempio viene installato quando si sceglie il carico di lavoro **sviluppo di applicazioni desktop con C++** nell'programma di installazione di Visual Studio. Per informazioni su come installare Visual Studio e scegliere carichi di lavoro specifici e singoli componenti, vedere [installare Visual Studio](../../install/install-visual-studio.md).

Quando è installato, l'esempio si trova nella directory di installazione di Visual Studio, in una sottodirectory denominata \DIA SDK\Samples\DIA2Dump.

## <a name="build-the-sample"></a>Compilare l'esempio

Per impostazione predefinita, la directory di installazione è una directory protetta. Ciò significa che è necessario usare un prompt dei comandi per gli sviluppatori con privilegi elevati o un'istanza di Visual Studio per compilare e modificare la soluzione di esempio in questa posizione. Per semplificare la compilazione, è consigliabile copiare prima i file dalla directory di esempio in un'altra directory, ad esempio una cartella nella cartella documenti, quindi compilare l'esempio.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Per compilare l'esempio Dia2Dump in Visual Studio

1. Aprire il file DIA2Dump. sln in Visual Studio. Se la soluzione non è stata copiata in un'altra directory, è possibile che venga richiesto di riavviare Visual Studio con autorizzazioni elevate.

1. In **Esplora soluzioni** selezionare il progetto Dia2Dump (non la soluzione).

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [Utilizzo di proprietà di progetto](/cpp/build/working-with-project-properties).

1. Aprire la pagina delle proprietà generale relativa alle **proprietà di configurazione**  >  **C/C++**  >   .

1. Nella proprietà **directory di inclusione aggiuntive** scegliere il controllo elenco a discesa, quindi scegliere **modifica**.

1. Nella finestra di dialogo **directory di inclusione aggiuntive** , nel campo modifica, immettere la `$(VSInstallDir)DIA SDK\include` Directory. Aggiungere questa directory per garantire che il compilatore possa trovare il file dia2. h. Scegliere **OK** per salvare le modifiche.

1. Scegliere **OK** per salvare le modifiche apportate alle proprietà del progetto.

1. Scegliere **Ricompila soluzione** dal menu **Compila** . Per impostazione predefinita, in Visual Studio viene compilata una versione di debug dell'esempio che si trova in una sottodirectory di debug della directory della soluzione.

1. Chiudere Visual Studio.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Per compilare l'esempio Dia2Dump dalla riga di comando

1. In una finestra del prompt dei comandi per gli sviluppatori passare alla directory in cui sono stati copiati i file di esempio. Se l'esempio non è stato copiato in un'altra directory, è necessario usare una finestra del prompt dei comandi per gli sviluppatori con privilegi elevati (Esegui come amministratore).

1. Immettere il comando `nmake makefile` per compilare la configurazione di debug predefinita del dia2dump.exe.

## <a name="run-the-dia2dump-sample"></a>Eseguire l'esempio Dia2Dump

Dia2Dump.exe si basa sul server COM *Version*. dll di MSDIA vengono per fornire i servizi. A partire da Visual Studio 2015, la versione è msdia140.dll. Se il server COM *Version*. dll di MSDIA vengono non è inizializzato, è necessario registrarlo prima che dia2dump.exe possa funzionare. La directory DIA SDK dispone di una sottodirectory bin che contiene la versione x86 della DLL. Una versione per computer con architettura x64 è in bin\amd64 e una versione per ARM si trova in bin\arm. Per registrare la dll, aprire una finestra del prompt dei comandi per gli sviluppatori con privilegi elevati e passare alla directory che contiene la versione per l'architettura del computer. Immettere il comando `regsvr32 msdia140.dll` per registrare il server com.

### <a name="to-run-the-sample"></a>Per eseguire l'esempio

1. Aprire un prompt dei comandi e passare alla directory che contiene il dia2dump.exe compilato.

1. Immettere il comando `dia2dump filename` dove *filename* è il nome di un file PDB da esaminare. Se il file PDB si trova in un'altra directory, utilizzare il percorso completo del file come *nome file*. Questo comando elenca tutti i dati nel file PDB.

1. Dia2Dump dispone di altre opzioni per visualizzare solo le informazioni selezionate. Usare il `dia2dump -?` comando per elencare tutte le opzioni disponibili.

## <a name="see-also"></a>Vedi anche

- [Porta, migrazione e aggiornamento dei progetti di Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)
