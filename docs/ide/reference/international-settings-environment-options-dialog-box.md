---
title: Impostazioni Impostazioni nella finestra di dialogo Opzioni
description: Informazioni su come usare la pagina Impostazioni internazionale nella sezione Ambiente per modificare la lingua predefinita quando sono installate più versioni linguistiche dell'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 0b0efa5a6afa002e935e67fe56586195c41979a5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101167"
---
# <a name="options-dialog-box-environment--international-settings"></a>Finestra di dialogo Opzioni: Ambiente \> internazionale Impostazioni

La pagina Impostazioni internazionali consente di modificare la lingua predefinita quando nel computer in uso sono installate più versioni in lingue diverse dell'IDE (Integrated Development Environment). È possibile accedere a questa finestra di dialogo selezionando **Opzioni** dal menu **Strumenti** e scegliendo **Impostazioni internazionali** dalla cartella **Ambiente**.

**Lingua**

Elenca le lingue disponibili per le versioni di lingua del prodotto installato. Se l'ambiente è condiviso da più lingue di prodotti o da un'installazione mista di lingue dei prodotti, la selezione della lingua viene modificata in **Come Microsoft Windows**.

> [!CAUTION]
> In un sistema con più lingue installate, gli strumenti di compilazione Visual C++ (cl.exe, link.exe, nmake.exe, bscmake.exe e file correlati) non sono interessati da questa impostazione. Questi strumenti usano la versione dell'ultima lingua installata. Gli strumenti di compilazione per la lingua precedentemente installata vengono sovrascritti perché gli strumenti di compilazione di Visual C++ non usano il modello DLL satellite.

### <a name="see-also"></a>Vedi anche

- [Installare i language pack](../../install/install-visual-studio.md#step-6---install-language-packs-optional)
