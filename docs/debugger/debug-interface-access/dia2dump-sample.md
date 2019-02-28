---
title: Esempio Dia2dump | Microsoft Docs
ms.date: 07/24/2018
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb86929a050a61a50a7aa1dd41220f4e087ad767
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56607044"
---
# <a name="dia2dump-sample"></a>Esempio Dia2dump

Esempio Dia2dump viene illustrato come utilizzare il Microsoft eseguire il Debug dell'interfaccia Access Software Development Kit (DIA SDK) per eseguire query di un file PDB per informazioni.

Esempio Dia2dump viene installato con Visual Studio e contiene i file di soluzione e origine. Il file eseguibile compilato viene eseguito dalla riga di comando. È possibile visualizzare il contenuto di un file di database (con estensione pdb) intero programma, o solo le sezioni si è interessati.

## <a name="install-the-sample"></a>Installare il campione

L'esempio viene installato quando si sceglie la **sviluppo di applicazioni Desktop con C++** carico di lavoro in Visual Studio Installer. Per informazioni su come installare Visual Studio e scegliere i singoli componenti e carichi di lavoro specifici, vedere [installazione di Visual Studio](../../install/install-visual-studio.md).

Durante l'installazione, l'esempio è nella directory di installazione di Visual Studio, in una sottodirectory denominata \DIA SDK\Samples\DIA2Dump.

## <a name="build-the-sample"></a>Compilare l'esempio

Per impostazione predefinita, la directory di installazione è una directory protetta. Pertanto, che è necessario usare un prompt con privilegi elevati per gli sviluppatori o un'istanza di Visual Studio per compilare e modificare la soluzione di esempio in questa posizione. Per semplificare la compilazione, è consigliabile innanzitutto copiare i file dalla directory di esempio in un'altra directory, ad esempio una cartella nella cartella documenti e quindi compilare l'esempio.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Per compilare l'esempio Dia2Dump in Visual Studio

1. Aprire il file DIA2Dump.sln in Visual Studio. Se la soluzione non è stato copiato in un'altra directory, potrebbe essere necessario riavviare Visual Studio con autorizzazioni elevate.

1. Nelle **Esplora soluzioni**, selezionare il progetto Dia2Dump (non sulla soluzione).

1. Aprire la finestra di dialogo **Pagine delle proprietà** del progetto. Per informazioni dettagliate, vedere [Utilizzo di proprietà di progetto](/cpp/ide/working-with-project-properties).

1. Aprire il **le proprietà di configurazione** > **C/C++** > **generale** pagina delle proprietà.

1. Nel **directory di inclusione aggiuntive** proprietà, scegliere il controllo a discesa, quindi scegliere **modificare**.

1. Nel **directory di inclusione aggiuntive** finestra di dialogo, nel campo di modifica, immettere il `$(VSInstallDir)DIA SDK\include` directory. Aggiungere la directory per garantire che il compilatore possa trovare il file dia2.h. Scegliere **OK** per salvare le modifiche.

1. Scegli **OK** per salvare le modifiche alle proprietà del progetto.

1. Nel **compilare** menu, scegliere **Ricompila soluzione**. Per impostazione predefinita, Visual Studio compila una versione di Debug dell'esempio, che si trova in una sottodirectory di Debug della directory della soluzione.

1. Chiudere Visual Studio.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Per compilare l'esempio Dia2Dump nella riga di comando

1. In una finestra del prompt dei comandi per gli sviluppatori, passare alla directory in cui è stato copiato i file di esempio. Se si non copia il codice di esempio in un'altra directory, è necessario utilizzare con privilegi elevati (Esegui come amministratore) finestra di prompt dei comandi per gli sviluppatori.

1. Immettere il comando `nmake makefile` per compilare la configurazione di Debug predefinito di dia2dump.exe.

## <a name="run-the-dia2dump-sample"></a>Eseguire l'esempio Dia2Dump

Dia2Dump.exe si basa sul msdia*versione*DLL COM server di fornire i servizi. In Visual Studio 2015 e Visual Studio 2017, la versione è msdia140.dll. Se il msdia*versione*server DLL COM non è inizializzato, è necessario registrarlo prima di poter utilizzare dia2dump.exe. La directory di DIA SDK ha una sottodirectory bin contenente x86 versione della DLL. Una versione per x64 macchine di architettura è in bin\amd64 e una versione per ARM è in bin\arm. Per registrare la dll, aprire una finestra del prompt dei comandi per gli sviluppatori con privilegi elevata e passare alla directory che contiene la versione per l'architettura del computer. Immettere il comando `regsvr32 msdia140.dll` per registrare il server COM.

### <a name="to-run-the-sample"></a>Per eseguire l'esempio

1. Aprire un prompt dei comandi e passare alla directory che contiene il dia2dump.exe compilato.

1. Immettere il comando `dia2dump filename` in cui *filename* è il nome di un file PDB da esaminare. Se il file PDB è in un'altra directory, usare il percorso completo del file come *filename*. Questo comando Elenca tutti i dati nel file PDB.

1. Dia2Dump offre altre opzioni per visualizzare esclusivamente alcune informazioni. Usare il `dia2dump -?` comando per elencare tutte le opzioni disponibili.

## <a name="see-also"></a>Vedere anche

- [Conversione, migrazione e aggiornamento dei progetti di Visual Studio](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)
