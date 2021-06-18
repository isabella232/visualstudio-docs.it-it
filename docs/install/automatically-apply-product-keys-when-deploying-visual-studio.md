---
title: Applicare automaticamente codici Product Key
description: Informazioni sulla procedura di applicazione dei codici Product Key a livello di programmazione durante la distribuzione di Visual Studio.
ms.date: 09/24/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: d79260be-6234-4fd3-89b5-a9756b4a93c1
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a78da89d8e8ce4251bc9288270628bfe784eca7a
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307717"
---
# <a name="automatically-apply-product-keys-when-deploying-visual-studio"></a>Applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio

È possibile applicare il codice Product Key a livello di programmazione come parte dello script utilizzato per automatizzare la distribuzione di Visual Studio. È possibile impostare i codici Product Key su un dispositivo a livello di programmazione durante l'installazione di Visual Studio o al termine dell'installazione.

::: moniker range=">=vs-2022"

> [!IMPORTANT]
> Visual Studio 2022 è attualmente in anteprima e durante il periodo di anteprima Visual Studio 2022 è disponibile con una licenza di valutazione che non richiede l'applicazione del codice Product Key.

::: moniker-end

::: moniker range="vs-2017"

## <a name="apply-the-license-after-installation"></a>Applicare la licenza dopo l'installazione

È possibile attivare una versione installata di Visual Studio con un codice Product Key tramite l'utilità `StorePID.exe` nei computer di destinazione in modalità invisibile all'utente. `StorePID.exe` è un programma di utilità che viene installato con Visual Studio 2017 nel percorso predefinito seguente:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE
```

 Eseguire `StorePID.exe` con privilegi elevati, usando un agente System Center o un prompt dei comandi con privilegi elevati. Continuare quindi con il codice Product Key (con i trattini) e il codice Microsoft Product Code (MPC).

>[!IMPORTANT]
> Assicurarsi di includere i trattini nel codice Product Key.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2019"

## <a name="apply-the-license-after-installation"></a>Applicare la licenza dopo l'installazione

È possibile attivare una versione installata di Visual Studio con un codice Product Key tramite l'utilità `StorePID.exe` nei computer di destinazione in modalità invisibile all'utente. `StorePID.exe` è un programma di utilità che viene installato con Visual Studio 2019 nel percorso predefinito seguente:

```shell
C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE
```

 Eseguire `StorePID.exe` con privilegi elevati, usando un agente System Center o un prompt dei comandi con privilegi elevati. Continuare quindi con il codice Product Key (con i trattini) e il codice Microsoft Product Code (MPC).

>[!IMPORTANT]
> Assicurarsi di includere i trattini nel codice Product Key.

 ```shell
 StorePID.exe [product key including the dashes] [MPC]
 ```

::: moniker-end

::: moniker range="vs-2017"

In questo esempio è riportata una riga di comando per l'applicazione della licenza di Visual Studio 2017 Enterprise, con codice MPC 08860 e codice Product Key `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, presupponendone l'installazione in un percorso predefinito:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 08860
```

::: moniker-end

::: moniker range="vs-2019"

In questo esempio è riportata una riga di comando per l'applicazione della licenza di Visual Studio 2019 Enterprise, con codice MPC 09260 e codice Product Key `AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE`, presupponendone l'installazione nel percorso predefinito:

```shell
"C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\StorePID.exe" AAAAA-BBBBB-CCCCC-DDDDDD-EEEEEE 09260
```

::: moniker-end

::: moniker range="vs-2017"

 La tabella seguente riporta i codici MPC per ogni edizione di Visual Studio:

| Edizione di Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2017        | 08860 |
| Visual Studio Professional 2017      | 08862 |
| Visual Studio Test Professional 2017 | 08866 |

::: moniker-end

::: moniker range="vs-2019"

| Edizione di Visual Studio                | MPC   |
|--------------------------------------|-------|
| Visual Studio Enterprise 2019        | 09260 |
| Visual Studio Professional 2019      | 09262 |

::: moniker-end

::: moniker range="vs-2017"

Se `StorePID.exe` applica correttamente il codice Product Key, restituisce un `%ERRORLEVEL%` pari a 0. Se si verificano errori, verrà restituito uno dei codici seguenti, a seconda della condizione di errore:

| Errore                     | Codice |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Quando si esegue un'istanza virtuale di Visual Studio, assicurarsi di virtualizzare anche la cartella AppData locale e il Registro di sistema. Per risolvere i problemi relativi alle istanze virtuali, eseguire `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe` .  

::: moniker-end

::: moniker range="vs-2019"

Se `StorePID.exe` applica correttamente il codice Product Key, restituisce un `%ERRORLEVEL%` pari a 0. Se si verificano errori, verrà restituito uno dei codici seguenti, a seconda della condizione di errore:

| Errore                     | Codice |
|---------------------------|------|
| `PID_ACTION_SUCCESS`      | 0    |
| `PID_ACTION_NOTINSTALLED` | 1    |
| `PID_ACTION_INVALID`      | 2    |
| `PID_ACTION_EXPIRED`      | 3    |
| `PID_ACTION_INUSE`        | 4    |
| `PID_ACTION_FAILURE`      | 5    |
| `PID_ACTION_NOUPGRADE`    | 6    |

> [!NOTE]
> Quando si esegue un'istanza virtuale di Visual Studio, assicurarsi di virtualizzare anche la cartella AppData locale e il Registro di sistema. Per risolvere i problemi relativi alle istanze virtuali, eseguire `<Visual Studio installation directory>\Common7\IDE\DDConfigCA.exe` .  

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Installa Visual Studio](../install/install-visual-studio.md)
* [Creare un'installazione offline di Visual Studio](../install/create-an-offline-installation-of-visual-studio.md)