---
description: Consente di importare, esportare o reimpostare le impostazioni di Visual Studio.
title: Importa/Esporta impostazioni (comando)
ms.date: 11/21/2018
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f2ea4811af2c44277b9a6dc285972c5267b28d7
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223673"
---
# <a name="import-and-export-settings-command"></a>Importa/Esporta impostazioni (comando)

Consente di importare, esportare o reimpostare le impostazioni di Visual Studio.

## <a name="syntax"></a>Sintassi

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Commutatori

/export:`filename`

facoltativo. Esporta le impostazioni correnti nel file specificato.

/import:`filename`

facoltativo. Importa le impostazioni correnti nel file specificato.

/reset

facoltativo. Reimposta le impostazioni correnti.

## <a name="remarks"></a>Commenti

Se si esegue questo comando senza opzioni viene visualizzata l'**Importazione/Esportazione guidata delle impostazioni**. Per altre informazioni, vedere [Sincronizzare le impostazioni](../synchronized-settings-in-visual-studio.md) e [Impostazioni dell'ambiente](../environment-settings.md).

## <a name="example"></a>Esempio

Il comando seguente esporta le impostazioni correnti nel file `MyFile.vssettings`:

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Vedi anche

- [Impostazioni dell'ambiente](../../ide/environment-settings.md)
- [Sincronizzare le impostazioni](../../ide/synchronized-settings-in-visual-studio.md)
- [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)
