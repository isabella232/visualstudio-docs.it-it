---
description: Consente di importare, esportare o reimpostare le impostazioni di Visual Studio. Estensione di file vssettings
title: Importa/Esporta impostazioni (comando)
ms.date: 05/28/2021
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: eb9c82d02a708d8aec49a620b836da6761594733c67b52cb04c1e4d7adfe62ae
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121372465"
---
# <a name="import-and-export-settings-command-vssettings-file"></a>Importare ed esportare Impostazioni comando (file con estensione vssettings)

Importa, esporta o reimposta Visual Studio file di impostazioni, `.vssettings` .

Lo schema del file è aperto. In genere, lo schema segue una struttura XML in cui ogni categoria è un tag, che a sua volta può contenere tag di sottocategoria. Questi tag di sottocategoria possono contenere tag di valori di proprietà. Anche se la maggior parte dei pacchetti usa la struttura comune, qualsiasi pacchetto Visual Studio può fornire codice XML arbitrario al file con lo schema scelto.

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
