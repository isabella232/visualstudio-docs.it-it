---
title: Recupero di log di compilazione con MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d372bf84d6b43547be160a50e52afffccd42bc89
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035575"
---
# <a name="obtain-build-logs-with-msbuild"></a>Recuperare log di compilazione con MSBuild

Usando le opzioni con MSBuild, è possibile specificare quanti dati di compilazione si vogliono esaminare e se salvare i dati di compilazione in uno o più file. È anche possibile specificare un logger personalizzato per raccogliere i dati di compilazione. Per informazioni sulle opzioni della riga di comando di MSBuild non illustrate in questo argomento, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).  
  
> [!NOTE]
> Se si compilano progetti usando l'IDE di Visual Studio, è possibile risolvere i problemi di tali compilazioni esaminando i log di compilazione. Per altre informazioni, vedere [Procedura: Visualizzare, salvare e configurare file di log di compilazione](../ide/how-to-view-save-and-configure-build-log-files.md).
  
## <a name="set-the-level-of-detail"></a>Impostare il livello di dettaglio  

 Quando si compila un progetto usando MSBuild senza specificare un livello di dettaglio, nel log di output vengono visualizzate le informazioni seguenti:  
  
- Errori, avvisi e messaggi classificati come molto importanti.  
  
- Alcuni eventi di stato.  
  
- Riepilogo della compilazione.  

Usando l'opzione **-verbosity** (**-v**), è possibile controllare la quantità di dati da visualizzare nel log di output. Per la risoluzione dei problemi, usare un livello di dettaglio `detailed` (`d`) o `diagnostic` (`diag`), che fornisce la maggior parte delle informazioni.  

Il processo di compilazione può essere più lento quando si imposta **-verbosity** su `detailed` e ancora più lento quando si imposta **-verbosity** su `diagnostic`.  

```cmd
msbuild MyProject.proj -t:go -v:diag  
```  

### <a name="verbosity-settings"></a>Impostazioni del livello di dettaglio

La tabella seguente illustra in che modo il livello di dettaglio del log (valori di colonna) influisce sulla scelta dei tipi di messaggio (valori di riga) da registrare.

|                                       | Quiet | Minimal | Normale | Dettagliato | Diagnostico |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| Errori                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Avvisi                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| Messaggi con priorità alta              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| Messaggi con priorità normale           |       |         |    ✅   |     ✅    |      ✅     |
| Messaggi con priorità bassa              |       |         |        |     ✅    |      ✅     |
| Informazioni aggiuntive sul motore di MSBuild |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>Salvare il log di compilazione in un file  

È possibile usare l'opzione **-fileLogger** (**fl**) per salvare i dati di compilazione in un file. L'esempio seguente salva i dati di compilazione in un file denominato *msbuild.log*.  

```cmd  
msbuild MyProject.proj -t:go -fileLogger  
```  

 Nell'esempio seguente il nome del file di log è *MyProjectOutput.log* e il dettaglio dell'output del log è impostato su `diagnostic`. Per specificare queste due impostazioni, è necessario usare l'opzione **-filelogparameters** (`flp`).  

```cmd  
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  

 Per altre informazioni, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).  
  
## <a name="save-the-log-output-to-multiple-files"></a>Salvare l'output del log in più file  

 L'esempio seguente salva l'intero log in *msbuild1.log*, i soli errori in *JustErrors.log* e i soli avvisi in *JustWarnings.log*. L'esempio usa numeri di file per ognuno dei tre file. I numeri di file vengono specificati subito dopo le opzioni **-fl** e **-flp**, ad esempio `-fl1` e `-flp1`.  
  
 Le opzioni **-filelogparameters** (`flp`) per i file 2 e 3 specificano il nome da assegnare a ogni file e che cosa includere in ogni file. Poiché per il file 1 non è specificato alcun nome, viene usato il nome predefinito *msbuild1.log*.  

```cmd  
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly  
```  

 Per altre informazioni, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).  

## <a name="save-a-binary-log"></a>Salvare un log binario

È possibile salvare il log in formato binario compresso usando l'opzione **-binaryLogger** (**bl**). Il log include una descrizione dettagliata del processo di compilazione e può essere letto da alcuni strumenti di analisi dei log.

Nell'esempio seguente viene creato un file di log binario con nome *binarylogfilename*.

```cmd  
/bl:binarylogfilename.binlog
``` 

Per altre informazioni, vedere [Riferimenti alla riga di comando](../msbuild/msbuild-command-line-reference.md).  

## <a name="use-a-custom-logger"></a>Usare un logger personalizzato  

 Per scrivere un logger personalizzato, è sufficiente creare un tipo gestito che implementi l'interfaccia <xref:Microsoft.Build.Framework.ILogger>. È possibile usare un logger personalizzato, ad esempio, per inviare gli errori di compilazione in un messaggio di posta elettronica, registrarli in un database o registrarli in un file XML. Per altre informazioni, vedere [Logger di compilazione](../msbuild/build-loggers.md).  
  
 Nella riga di comando di MSBuild è possibile specificare il logger personalizzato tramite l'opzione **-logger**. È anche possibile usare l'opzione **-noconsolelogger** per disabilitare il logger di console predefinito.  
  
## <a name="see-also"></a>Vedere anche  

 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [Logger di compilazione](../msbuild/build-loggers.md)   
 [Registrazione in un ambiente a più processori](../msbuild/logging-in-a-multi-processor-environment.md)   
 [Creazione di logger di inoltro](../msbuild/creating-forwarding-loggers.md)   
 [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)