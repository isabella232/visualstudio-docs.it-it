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
ms.workload:
- multiple
ms.openlocfilehash: dba50cf598c3c74f6c9407fbef5d55f938941a11
ms.sourcegitcommit: 63cb90e8cea112aa2ce8741101b309dbc709e393
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2021
ms.locfileid: "110687639"
---
# <a name="import-and-export-settings-command-vssettings-file"></a>Comando Importa/Esporta impostazioni (file con estensione vssettings)

Importa, esporta o reimposta Visual Studio file di impostazioni, `.vssettings` .

Lo schema del file è aperto. In genere, lo schema segue una struttura XML in cui ogni categoria è un tag, che a sua volta può contenere tag di sottocategoria. Questi tag di sottocategoria possono contenere tag di valori di proprietà. Sebbene la maggior parte dei pacchetti usi la struttura comune, qualsiasi pacchetto in Visual Studio può fornire codice XML arbitrario al file con lo schema scelto.

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
