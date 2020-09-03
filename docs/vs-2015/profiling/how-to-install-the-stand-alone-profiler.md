---
title: 'Procedura: Installare il profiler autonomo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 026162a2c8334c7163f9c7853d2de30e58e5939a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "77476794"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>Procedura: installare il profiler autonomo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] offre un profiler autonomo basato sulla riga di comando che può essere eseguito senza installare l'IDE di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Questa situazione si verifica quando un computer non ha o non può avere un ambiente di sviluppo installato. È consigliabile, ad esempio, non installare un ambiente di sviluppo in un server Web di produzione.  
  
> [!NOTE]
> Quando si usa il profiler autonomo per raccogliere dati sulle prestazioni per il sito Web ASP.NET, è consigliabile usare lo strumento da riga di comando [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) anziché lo strumento [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-install-the-stand-alone-profiler"></a>Per installare il profiler autonomo  
  
1. Individuare il programma di installazione del profiler autonomo (vs_profiler.exe) nei supporti di installazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nella directory che include il percorso \Standalone Profiler ed eseguirlo.  
  
2. Aggiungere i percorsi per vsintr.exe e msdis150.dll al percorso di sistema.  
  
    > [!NOTE]
    > Nell'installazione predefinita di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] vsinstr.exe e msdis150.dll si trovano in \Programmi\Visual Studio 10\Team Tools\Performance Tools.  
  
3. Al prompt dei comandi digitare **VSInstr**.  
  
    > [!NOTE]
    > Se vengono visualizzate le informazioni di utilizzo per vsinstr.exe, significa che tutti gli elementi sono configurati correttamente. Se viene visualizzato un errore in cui viene comunicato che vsinstr.exe o una delle relative dipendenze non è stata trovata, verificare di aver specificato correttamente i percorsi come descritto nel passaggio 2.  
  
4. Configurare il server dei simboli impostando la variabile di **_NT_SYMBOL_PATH** su `symsrv*symsrv.dll*c:\localcache*https://msdl.microsoft.com/download/symbols`  
  
5. Dopo aver impostato il server dei simboli usando le variabili di ambiente di sistema, eseguire gli strumenti del profiler da riga di comando in un nuovo prompt dei comandi. In questo modo le nuove variabili di ambiente vengono rese effettive. Nella finestra del prompt dei comandi digitare il comando seguente:  
  
     **start %COMSPEC%**  
  
    > [!NOTE]
    > Per istruzioni dettagliate su come configurare il pacchetto del server di simboli, vedere [procedura: fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md).  
  
6. Usare lo strumento [VSPerfReport](../profiling/vsperfreport.md) per serializzare i simboli nel file dei dati di profilatura (con estensione vsp). Usare le opzioni **VSPerfReport /summary:all /packsymbols**. Se non sono presenti simboli inseriti nel file di dati, assicurarsi di aver impostato la variabile di ambiente _NT_SYMBOL_PATH.  
  
## <a name="see-also"></a>Vedere anche  
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)   
 [Procedura dettagliata: profilatura dalla riga di comando tramite campionamento](../profiling/walkthrough-command-line-profiling-using-sampling.md)   
 [Procedura dettagliata: profilatura dalla riga di comando tramite strumentazione](../profiling/walkthrough-command-line-profiling-using-instrumentation.md)   
 [Procedura: fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
