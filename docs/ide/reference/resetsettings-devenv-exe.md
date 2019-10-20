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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3549801001ba8df60634884dc58137a8fa77d905
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655559"
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

## <a name="arguments"></a>argomenti

- *SettingsFile*

  Parametro facoltativo. Percorso completo e nome del file di impostazioni da applicare a Visual Studio.

- *DefaultCollectionSpecifier*

  Parametro facoltativo. Identificatore che rappresenta una raccolta predefinita di impostazioni da ripristinare. Scegliere uno degli identificatori delle raccolte predefinite elencati nella tabella.

  | Nome della raccolta predefinita | Identificatore della raccolta |
  | --- | --- |
  | **Generalee** | `General` |
  | **JavaScript** | `JavaScript` |
  | **Visual Basic** | `VB` |
  | **Visual C#** | `CSharp` |
  | **Visual C++** | `VC` |
  | **Sviluppo Web** | `Web` |
  | **Sviluppo Web (solo codice)** | `WebCode` |

## <a name="remarks"></a>Note

Se non viene specificato alcun *SettingsFile*, l'IDE viene aperto usando le impostazioni esistenti.

## <a name="example"></a>Esempio

Il primo esempio applica le impostazioni archiviate nel file `MySettings.vssettings`.

Il secondo esempio ripristina il profilo predefinito di Visual C#.

```shell
devenv /resetsettings "%USERPROFILE%\MySettings.vssettings"

devenv /resetsettings CSharp
```

## <a name="see-also"></a>Vedere anche

- [Impostazioni dell'ambiente](../environment-settings.md)
- [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)