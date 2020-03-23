---
title: -ResetSettings (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
- settings [Visual Studio], resetting
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eebcf2c6796723e51c3aefdb12575aa89779429f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593863"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)

Ripristina le impostazioni predefinite di Visual Studio e avvia in automatico IDE di Visual Studio. Questa opzione reimposta facoltativamente le impostazioni in un file di impostazioni specificato.

Le impostazioni predefinite derivano dal profilo selezionato al primo avvio di Visual Studio.

> [!TIP]
> Per informazioni su come reimpostare le impostazioni usando l'ambiente di sviluppo integrato (IDE), vedere [Reimpostare le impostazioni](../environment-settings.md#reset-settings).

## <a name="syntax"></a>Sintassi

```shell
devenv /ResetSettings [SettingsFile|DefaultCollectionSpecifier]
```

## <a name="arguments"></a>Argomenti

- *SettingsFile*

  Facoltativa. Percorso completo e nome del file di impostazioni da applicare a Visual Studio.

- *DefaultCollectionSpecifier*

  Facoltativa. Identificatore che rappresenta una raccolta predefinita di impostazioni da ripristinare. Scegliere uno degli identificatori delle raccolte predefinite elencati nella tabella.

  | Nome della raccolta predefinita | Identificatore della raccolta |
  | --- | --- |
  | **Generale** | `General` |
  | **Javascript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visuale C #** | `CSharp` |
  | **Visual C** | `VC` |
  | **Sviluppo Web** | `Web` |
  | **Sviluppo Web (solo codice)** | `WebCode` |

## <a name="remarks"></a>Osservazioni

Se non viene specificato alcun *SettingsFile*, l'IDE viene aperto usando le impostazioni esistenti.

## <a name="example"></a>Esempio

Il primo esempio applica le impostazioni archiviate nel file `MySettings.vssettings`.

Il secondo esempio ripristina il profilo predefinito di Visual C#.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Vedere anche

- [Impostazioni di ambiente](../environment-settings.md)
- [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)
