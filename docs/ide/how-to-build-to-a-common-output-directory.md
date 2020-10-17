---
title: 'Procedura: Compilare in una directory di output comune'
description: Informazioni su come è possibile modificare i percorsi di output di compilazione dei progetti per forzare l'inserimento di tutti gli output nella stessa cartella.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- output directory
- builds [Visual Studio], common directory
- common directory
ms.assetid: 1fcc2c48-07cb-4c4f-9556-36945e7dfc4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a39dae210c2cb9afe3e4b77962b75ddb3be4baeb
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136966"
---
# <a name="how-to-build-to-a-common-output-directory"></a>Procedura: Compilare in una directory di output comune

Per impostazione predefinita, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] compila ogni progetto in una soluzione nella relativa cartella all'interno della soluzione. È possibile modificare i percorsi di output di compilazione dei progetti per inserire tutti gli output nella stessa cartella.

## <a name="to-place-all-solution-outputs-in-a-common-directory"></a>Per inserire tutti gli output della soluzione in una directory comune

1. Fare clic su un progetto nella soluzione.

2. Scegliere **Proprietà** dal menu **Progetto**.

3. A seconda del tipo di progetto, fare clic sulla scheda **Compila** o **Build** e impostare il **Percorso di output** su una cartella da usare per tutti i progetti della soluzione.

4. Ripetere i passaggi da 1 a 3 per tutti i progetti della soluzione.

## <a name="see-also"></a>Vedere anche

- [Compilare](../ide/compiling-and-building-in-visual-studio.md)
- [Procedura: modificare la directory dell'output di compilazione](../ide/how-to-change-the-build-output-directory.md)