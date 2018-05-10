---
title: -ResetSettings (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
ms.openlocfilehash: 3c3d3a6ef558b510cfde716716daf97a549fbba4
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Ripristina le impostazioni predefinite di Visual Studio e avvia in automatico IDE di Visual Studio. Facoltativamente, reimposta le impostazioni in un file con estensione *vssettings* specificato.

Le impostazioni predefinite sono determinate dal profilo che è stato selezionato quando Visual Studio è stato avviato per la prima volta.

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

- [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)