---
title: Importa/Esporta impostazioni (comando)
ms.date: 11/21/2018
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0be61d8690c0605f6e7773efe02f5db351110f9a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658769"
---
# <a name="import-and-export-settings-command"></a>Importa/Esporta impostazioni (comando)

Consente di importare, esportare o reimpostare le impostazioni di Visual Studio.

## <a name="syntax"></a>Sintassi

```cmd
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]
```

## <a name="switches"></a>Opzioni

/export:`filename`

Parametro facoltativo. Esporta le impostazioni correnti nel file specificato.

/import:`filename`

Parametro facoltativo. Importa le impostazioni correnti nel file specificato.

/reset

Parametro facoltativo. Reimposta le impostazioni correnti.

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