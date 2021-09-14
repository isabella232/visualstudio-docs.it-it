---
description: L'esempio Dia2dump illustra come usare Microsoft Debug Interface Access Software Development Kit (DIA SDK) per eseguire query su un file PDB per ottenere informazioni.
title: Esempio di Dia2dump | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: cdf5e84eaeace022d733d7f8521aecdbc2cd58d1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630647"
---
# <a name="dia2dump-sample"></a>Esempio Dia2dump

L'esempio Dia2dump illustra come usare Microsoft Debug Interface Access Software Development Kit (DIA SDK) per eseguire query su un file PDB per ottenere informazioni.

L'esempio Dia2dump viene installato con Visual Studio e contiene i file di soluzione e di origine. Il file eseguibile compilato viene eseguito dalla riga di comando. Può visualizzare il contenuto di un intero file di database di programma (con estensione pdb) o solo le sezioni a cui si è interessati.

## <a name="install-the-sample"></a>Installare l'esempio

L'esempio viene installato quando si sceglie il carico di lavoro Sviluppo di applicazioni desktop con **C++** nel Programma di installazione di Visual Studio. Per informazioni su come installare Visual Studio e scegliere carichi di lavoro specifici e singoli componenti, vedere [Installare Visual Studio](../../install/install-visual-studio.md).

Al termine dell'installazione, l'esempio si trova nella directory di installazione Visual Studio, in una sottodirectory denominata \DIA SDK\Samples\DIA2Dump.

## <a name="build-the-sample"></a>Compilare l'esempio

Per impostazione predefinita, la directory di installazione è una directory protetta. Ciò significa che è necessario usare un prompt dei comandi per gli sviluppatori con privilegi elevati o un'istanza di Visual Studio per compilare e modificare la soluzione di esempio in questo percorso. Per semplificare la compilazione, è consigliabile copiare prima i file dalla directory di esempio in un'altra directory, ad esempio una cartella nella cartella Documenti, quindi compilare l'esempio.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Per compilare l'esempio Dia2Dump in Visual Studio

1. Aprire il file DIA2Dump.sln in Visual Studio. Se la soluzione non è stata copiata in un'altra directory, potrebbe essere richiesto di riavviare Visual Studio con autorizzazioni elevate.

1. In **Esplora soluzioni** selezionare il progetto Dia2Dump (non la soluzione).

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [Utilizzo di proprietà di progetto](/cpp/build/working-with-project-properties).

1. Aprire la **pagina delle proprietà Generale** di Proprietà di configurazione  >  **C/C++.**  >  

1. Nella proprietà **Directory di inclusione aggiuntive** scegliere il controllo elenco a discesa, quindi scegliere **Modifica.**

1. Nella finestra **di dialogo Directory di** inclusione aggiuntive immettere la directory nel campo di `$(VSInstallDir)DIA SDK\include` modifica. Aggiungere questa directory per garantire che il compilatore possa trovare il file dia2.h. Scegliere **OK** per salvare le modifiche.

1. Scegliere **OK** per salvare le modifiche apportate alle proprietà del progetto.

1. Scegliere **Ricompila** **soluzione dal** menu Compila . Per impostazione predefinita, Visual Studio compila una versione di debug dell'esempio, che si trova in una sottodirectory Debug della directory della soluzione.

1. Chiudere Visual Studio.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Per compilare l'esempio Dia2Dump dalla riga di comando

1. In una finestra del prompt dei comandi per gli sviluppatori passare alla directory in cui sono stati copiati i file di esempio. Se l'esempio non è stato copiato in un'altra directory, è necessario usare una finestra del prompt dei comandi per gli sviluppatori con privilegi elevati (Esegui come amministratore).

1. Immettere il comando `nmake makefile` per compilare la configurazione di debug predefinita di dia2dump.exe.

## <a name="run-the-dia2dump-sample"></a>Eseguire l'esempio Dia2Dump

Dia2Dump.exe si basa sulla versione *msdia*.dll server COM per fornire i propri servizi. A partire Visual Studio 2015, la versione è msdia140.dll. Se la versione di *msdia*.dll server COM non è inizializzata, è necessario registrarla prima dia2dump.exe possibile funzionare. La DIA SDK directory contiene una sottodirectory bin che contiene la versione x86 della DLL. Una versione per i computer con architettura x64 è in bin\amd64 e una versione per ARM si trova in bin\arm. Per registrare la DLL, aprire una finestra del prompt dei comandi per gli sviluppatori con privilegi elevati e passare alla directory contenente la versione per l'architettura del computer. Immettere il comando `regsvr32 msdia140.dll` per registrare il server COM.

### <a name="to-run-the-sample"></a>Per eseguire l'esempio

1. Aprire un prompt dei comandi e passare alla directory che contiene il dia2dump.exe creato.

1. Immettere il comando `dia2dump filename` dove *nomefile* è il nome di un file PDB da esaminare. Se il file PDB si trova in un'altra directory, usare il percorso completo del file come *nome file*. Questo comando elenca tutti i dati nel file PDB.

1. Dia2Dump include altre opzioni per visualizzare solo le informazioni selezionate. Usare il `dia2dump -?` comando per elencare tutte le opzioni disponibili.

## <a name="see-also"></a>Vedi anche

- [Eseguire la portabilità, la migrazione e l'aggiornamento Visual Studio progetti](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)
