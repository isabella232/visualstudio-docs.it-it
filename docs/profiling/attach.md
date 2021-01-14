---
title: Attach | Microsoft Docs
description: Usare l'opzione di connessione di VSPerfCmd.exe per avviare la profilatura del processo in esecuzione specificato dall'ID processo (PID).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: c97dee50d58b49092d9b23a497192b29746e0c22
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205697"
---
# <a name="attach"></a>Allega
L'opzione *Attach di* **VSPerfCmd.exe** avvia una profilatura campione del processo in esecuzione specificato dall'ID processo (PID).

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

 **Inizio:** `Method` Inizializza la sessione del profiler da riga di comando e imposta il metodo di profilatura specificato.

 **TargetCLR** Specifica la versione di Common Language Runtime (CLR) di .NET Framework da sottoporre a profilatura quando in una sessione di profilatura è caricata più di una versione. Per impostazione predefinita, viene sottoposta a profilatura la prima versione caricata.

 **GlobalOn GlobalOff** Riprende (**GlobalOn**) o sospende (**GlobalOff**) la profilatura, ma non termina la sessione di profilatura.

 **ProcessOn:** `PID` **ProcessOff:** `PID` Riprende **(processon) o** sospende (**ProcessOff**) la profilatura per il processo specificato.

## <a name="interval-options"></a>Opzioni di intervallo
 È possibile specificare una delle opzioni seguenti per l'intervallo di campionamento nella riga di comando di Attach. L'intervallo di campionamento predefinito è 10.000.000 di cicli di clock del processore.

 **Timer**[**:** `Cycles` ]**PF**[**:** `Events` ]**sys**[<strong>:</strong>Events]**Counter**[**:** `Name` , `Reload` , `FriendlyName` ] specifica il numero e il tipo dell'intervallo di campionamento.

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

## <a name="see-also"></a>Vedere anche
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Sottoporre a profilatura applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Sottoporre a profilatura applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Sottoporre a profilatura i servizi](../profiling/command-line-profiling-of-services.md)
