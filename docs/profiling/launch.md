---
title: Launch | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3afc0a50847591445c106d86460ee1821fe0df81
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219198"
---
# <a name="launch"></a>Launch
L'opzione **Launch** avvia il profiler usando il metodo di campionamento e avvia anche l'applicazione specificata.  
  
 Per usare l'opzione **Launch**, è necessario specificare il metodo **Sample** nell'opzione **Start**.  
  
## <a name="syntax"></a>Sintassi  
  
```cmd  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### <a name="parameters"></a>Parametri  
 `AppName`  
 Nome dell'applicazione da avviare. Sono supportati percorsi completi e parziali dalla directory corrente.  
  
## <a name="valid-options"></a>Opzioni valide  
 Le seguenti opzioni di VSPerfCmd possono essere combinate con l'opzione **Launch** in una singola riga di comando.  
  
 **Start:** `Method`  
 Inizializza la sessione del profiler da riga di comando e imposta il metodo di profilatura specificato.  
  
 **GlobalOn** e **GlobalOff**  
 Riprende (**GlobalOn**) o sospende (**GlobalOff**) la profilatura, ma non termina la sessione di profilatura.  
  
 **ProcessOn:** `PID` e **ProcessOff**:`PID`  
 Riprende (**ProcessOn**) o sospende (**ProcessOff**) la profilatura per il processo specificato.  
  
 **TargetCLR**  
 Specifica la versione di Common Language Runtime (CLR) .NET Framework da sottoporre a profilatura quando in una sessione di profilatura è caricata più di una versione. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.  
  
## <a name="exclusive-options"></a>Opzioni esclusive  
 È possibile usare le opzioni seguenti solo con l'opzione **Launch**.  
  
 **Console**  
 Avvia l'applicazione della riga di comando specificata in una nuova finestra.  
  
 **Args:** `ArgList`  
 Specifica l'elenco di argomenti da passare all'applicazione.  
  
 **LineOff**  
 Disabilita la raccolta dei dati di profilatura a livello di riga.  
  
## <a name="sampling-options"></a>Opzioni di campionamento  
 È possibile specificare una delle opzioni seguenti per l'intervallo di campionamento nella riga di comando di **Launch**. L'intervallo di campionamento predefinito è 10.000.000 cicli di clock del processore.  
  
 **Timer**[**:**`Cycles`]**PF**[**:**`Events`]**Sys**[**:**`Events`]**Counter**[**:**`Name`,`Reload`,`FriendlyName`]**GC**[:**allocation**&#124;**lifetime**]  
 Specifica il numero e tipo di intervallo di campionamento.  
  
-   **Timer**: esegue il campionamento di ogni `Cycles` dei cicli di clock del processore non interrotti. Se non si specifica `Cycles`, vengono usati 10.000.000 di cicli.  
  
-   **PF**: esegue il campionamento di ogni `Events` errori di pagina. Se non si specifica `Events`, vengono usati 10 errori di pagina.  
  
-   **Sys**: esegue il campionamento di ogni `Events` chiamate del sistema operativo. Se non si specifica `Events`, vengono usate 10 chiamate del sistema.  
  
-   **Counter**: esegue il campionamento ogni `Reload` dei contatori delle prestazioni della CPU specificato da `Name`. Facoltativamente, `FriendlyName` può specificare una stringa da usare come intestazione di colonna nei report del profiler.  
  
-   **GC**: raccoglie dati di memoria .NET. Per impostazione predefinita, (**allocation**), i dati vengono raccolti in corrispondenza di ogni evento di allocazione di memoria. Quando si specifica il parametro **lifetime**, i dati vengono raccolti anche in corrispondenza di ogni evento di Garbage Collection.  
  
## <a name="example"></a>Esempio  
 Questo esempio illustra l'uso di **Launch** per avviare un'applicazione.  
  
```cmd  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)