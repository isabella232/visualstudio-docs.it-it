---
title: -ResetSettings (devenv.exe)
ms.date: 11/16/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 160cbf93cee8ff778a4f84ee833c7fac3d7f26b1
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830664"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Ripristina le impostazioni predefinite di Visual Studio e avvia in automatico IDE di Visual Studio. Facoltativamente, reimposta le impostazioni in un file con estensione *vssettings* specificato.

Le impostazioni predefinite sono determinate dal profilo che è stato selezionato quando Visual Studio è stato avviato per la prima volta.

> [!TIP]
> Per informazioni su come reimpostare le impostazioni usando l'ambiente di sviluppo integrato (IDE), vedere [Reimpostare le impostazioni](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Sintassi

```cmd
Devenv /ResetSettings SettingsFile
```

## <a name="arguments"></a>Argomenti

`SettingsFile`

Il percorso completo e il nome del file con estensione *vssettings* da applicare a Visual Studio.

Per ripristinare il profilo Impostazioni generali per lo sviluppo, usare `General`.

## <a name="remarks"></a>Note

Se non viene specificato `SettingsFile`, al successivo avvio di Visual Studio verrà richiesto di selezionare una raccolta predefinita di impostazioni.

## <a name="example"></a>Esempio

La riga di comando seguente applica le impostazioni memorizzate nel file `MySettings.vssettings`.

```cmd
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"
```

## <a name="see-also"></a>Vedere anche

- [Impostazioni dell'ambiente](../environment-settings.md)
- [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)