---
title: Importa/Esporta impostazioni (comando)
ms.date: 11/21/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f5c011c1bbaaa66e3da39c7ca8d713099d11e5a4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041685"
---
# <a name="import-and-export-settings-command"></a>Importa/Esporta impostazioni (comando)

Consente di importare, esportare o reimpostare le impostazioni di Visual Studio.

## <a name="syntax"></a>Sintassi

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Opzioni

/export:`filename`

Facoltativo. Esporta le impostazioni correnti nel file specificato.

/import:`filename`

Facoltativo. Importa le impostazioni correnti nel file specificato.

/reset

Facoltativo. Reimposta le impostazioni correnti.

## <a name="remarks"></a>Note

Se si esegue questo comando senza opzioni viene visualizzata l'**Importazione/Esportazione guidata delle impostazioni**. Per altre informazioni, vedere [Sincronizzare le impostazioni](../synchronized-settings-in-visual-studio.md) e [Impostazioni dell'ambiente](../environment-settings.md).

## <a name="example"></a>Esempio

Il comando seguente esporta le impostazioni correnti nel file `MyFile.vssettings`:

```cmd
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>Vedere anche

- [Impostazioni dell'ambiente](../../ide/environment-settings.md)
- [Sincronizzare le impostazioni](../../ide/synchronized-settings-in-visual-studio.md)
- [Personalizzare l'IDE di Visual Studio](../../ide/personalizing-the-visual-studio-ide.md)
- [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)