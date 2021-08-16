---
title: Attach | Microsoft Docs
description: Usare l'opzione Collega VSPerfCmd.exe per avviare la profilatura del processo in esecuzione specificato dall'ID processo (PID).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 04c21ccedcac25214c3620f0c1fc4c69be5837bcd57e40b2727e8de2403952da
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427223"
---
# <a name="attach"></a>Collegamento
 **LVSPerfCmd.exe'opzione Collega** avvia la profilatura di esempio del processo in esecuzione specificato dall'ID processo (PID).

 Per usare l'opzione **Attach**, è necessario specificare il metodo **Sample** nell'opzione Start.

> [!NOTE]
> Se l'opzione **Start** è stata specificata con l'opzione **Crosssession**, eventuali chiamate a **VSPerfCmd /Attach** o a **VSPerfCmd /Detach** devono specificare anche **Crosssession**.

## <a name="syntax"></a>Sintassi

```cmd
VSPerfCmd.exe /Attach:ProcessID [Options]
```

#### <a name="parameters"></a>Parametri
 `ProcessID` ID di processo (PID) del processo in esecuzione. Il PID di un processo in esecuzione è indicato nella scheda Processi di Gestione attività di Windows.

## <a name="valid-options"></a>Opzioni valide
 Le seguenti opzioni di **VSPerfCmd** possono essere combinate con l'opzione **Attach** in una singola riga di comando.

 **Crosssession** Consente la profilatura delle applicazioni in sessioni diverse da quella di accesso. Obbligatoria se l'opzione **Start** è stata specificata con l'opzione **Crosssession**.

 **Avvio:** `Method` Inizializza la sessione del profiler della riga di comando e imposta il metodo di profilatura specificato.

 **TargetCLR** Specifica la versione di Common Language Runtime (CLR) di .NET Framework da sottoporre a profilatura quando in una sessione di profilatura è caricata più di una versione. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.

 **GlobalOn GlobalOff** Riprende (**GlobalOn**) o sospende (**GlobalOff**) la profilatura, ma non termina la sessione di profilatura.

 **ProcessOn:** `PID` **ProcessOff:** `PID` Riprende (**ProcessOn**) o sospende (**ProcessOff**) la profilatura per il processo specificato.

## <a name="interval-options"></a>Opzioni di intervallo
 È possibile specificare una delle opzioni seguenti per l'intervallo di campionamento nella riga di comando di Attach. L'intervallo di campionamento predefinito è 10.000.000 di cicli di clock del processore.

 **Timer**[**:**] PF [ : ] Sys [ : Events] Counter [ : , ] Specifica il numero e il `Cycles` tipo `Events` <strong></strong> `Name` `Reload` `FriendlyName` dell'intervallo di campionamento.

- **Timer**: esegue il campionamento ogni `Cycles` cicli di clock del processore. Se non si specifica `Cycles`, vengono usati 10.000.000 di cicli.

- **PF**: esegue il campionamento di ogni `Events` errori di pagina. Se non si specifica `Events`, vengono usati 10 errori di pagina.

- **Sys**: esegue il campionamento ogni `Events` chiamate al sistema operativo. Se non si specifica `Events`, vengono usate 10 chiamate del sistema.

- **Counter**: esegue il campionamento ogni `Reload` dei contatori delle prestazioni della CPU specificato da `Name`. Facoltativamente, `FriendlyName` può specificare una stringa da usare come intestazione di colonna nei rapporti del profiler.

## <a name="example"></a>Esempio
 In questo esempio viene illustrato come connettersi a un'istanza di un'applicazione in esecuzione con ID processo 12345.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Attach:12345
```

## <a name="see-also"></a>Vedi anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
