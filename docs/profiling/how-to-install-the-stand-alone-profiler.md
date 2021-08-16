---
title: Installare il profiler autonomo | Microsoft Docs
description: Informazioni su come installare il profiler autonomo, che può essere eseguito senza Visual Studio installato. Esistono situazioni in cui Visual Studio non deve essere installato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4aa55e3a5137122fd73f11ed5a2acb422e6c4b128926f40d8e1dfbb9817f6935
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410723"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Procedura: Installare il profiler autonomo
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] offre un profiler autonomo basato sulla riga di comando che può essere eseguito senza installare l'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Questa situazione si verifica quando un computer non ha o non può avere un ambiente di sviluppo installato. È consigliabile, ad esempio, non installare un ambiente di sviluppo in un server Web di produzione.

> [!NOTE]
> Quando si usa il profiler autonomo per raccogliere dati sulle prestazioni per un sito Web ASP.NET, è consigliabile usare lo strumento da riga di comando [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) anziché lo strumento [VSPerfCmd](../profiling/vsperfcmd.md).

### <a name="to-install-the-stand-alone-profiler"></a>Per installare il profiler autonomo

1. Scaricare gli [strumenti per le prestazioni di Visual Studio](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio).

1. Individuare il programma di installazione del profiler autonomo (*vs_standaloneprofiler.exe*) nel percorso in cui sono stati scaricati gli strumenti per le prestazioni ed eseguirlo.

2. Aggiungere il percorso per *vsinstr.exe* al percorso di sistema.

   > [!NOTE]
   > Per ottenere il percorso degli strumenti di profilatura, vedere [Specificare il percorso degli strumenti da riga di comando](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). Nei computer a 64 bit sono disponibili sia la versione a 32 bit che la versione a 64 bit degli strumenti. Per usare gli strumenti da riga di comando del profiler, è necessario aggiungere il percorso degli strumenti alla variabile di ambiente PATH della finestra del prompt dei comandi oppure aggiungerlo al comando stesso.

3. Al prompt dei comandi digitare **VSInstr**.

   > [!NOTE]
   > Se vengono visualizzate le informazioni di utilizzo per vsinstr.exe, significa che tutti gli elementi sono configurati correttamente. Se viene visualizzato un errore in cui viene comunicato che vsinstr.exe o una delle relative dipendenze non è stata trovata, verificare di aver specificato correttamente i percorsi come descritto nel passaggio 2.

4. Specificare il server dei simboli impostando la variabile **_NT_SYMBOL_PATH** su **symsrv\*symsrv.dll\*c:\localcache\*https://msdl.microsoft.com/download/symbols**

5. Dopo aver impostato il server dei simboli usando le variabili di ambiente di sistema, eseguire gli strumenti del profiler da riga di comando in un nuovo prompt dei comandi. In questo modo le nuove variabili di ambiente vengono rese effettive. Nella finestra del prompt dei comandi digitare il comando seguente:

    **start %COMSPEC%**

   > [!NOTE]
   > Per istruzioni dettagliate su come impostare il pacchetto del server dei simboli, vedere [Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md).

6. Usare lo strumento [VSPerfReport](../profiling/vsperfreport.md) per serializzare i simboli nel file dei dati di profilatura (con estensione vsp). Usare le opzioni **VSPerfReport /summary:all /packsymbols**. Se non sono presenti simboli inseriti nel file di dati, assicurarsi di aver impostato la variabile di ambiente _NT_SYMBOL_PATH.

## <a name="see-also"></a>Vedi anche
- [Usare gli strumenti per la profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)
- [Procedura dettagliata: Profilatura da riga di comando tramite strumentazione](command-line-profiling-of-stand-alone-applications.md)
- [Procedura: Fare riferimento alle Windows simboli](../profiling/how-to-reference-windows-symbol-information.md)
- [VSPerfReport](../profiling/vsperfreport.md)
