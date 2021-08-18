---
title: Selezionare un'impostazione di esecuzione per un test di carico
description: Un test di carico può includere impostazioni di esecuzione ovvero proprietà che determinano la modalità di esecuzione del test di carico. Informazioni su come selezionare l'impostazione di esecuzione attiva.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, run settings, active
ms.assetid: ed6ff546-acfa-4dd8-b3a2-6e7455930ca4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 0f85602761444283f13a32ef3709a1e417c46d9a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047413"
---
# <a name="how-to-select-the-active-run-setting-for-a-load-test"></a>Procedura: Selezionare l'impostazione di esecuzione test attiva per un test di carico

Dopo avere creato il test di carico mediante la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà degli scenari in modo da soddisfare le necessità e gli obiettivi di test.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

In un test di carico possono essere contenute una o più *impostazioni esecuzione test*, ovvero un set di proprietà che determinano la modalità di esecuzione del test di carico. Sono organizzate in categorie nella finestra **Proprietà**. Quando si esegue un test di carico, viene utilizzata l'impostazione esecuzione test impostata correntemente come attiva.

> [!NOTE]
> Per un elenco completo delle proprietà delle impostazioni di esecuzione e delle relative descrizioni, vedere [Proprietà delle impostazioni esecuzione test di carico](../test/load-test-run-settings-properties.md).

Se il test di carico contiene solo un nodo di impostazioni di esecuzione nella cartella **Impostazioni di esecuzione**, il nodo sarà sempre il nodo attivo. Se il test di carico contiene più nodi di impostazioni di esecuzione, è possibile selezionare quello da utilizzare per l'esecuzione di un test di carico. Vedere [Procedura: Aggiungere impostazioni di esecuzione a un test di carico](../test/how-to-add-additional-run-settings-to-a-load-test.md).

Nell'**Editor test di carico** l'impostazione di esecuzione attiva è identificata dal suffisso "[Active]".

## <a name="select-the-active-run-setting"></a>Selezionare l'impostazione di esecuzione attiva

1. Aprire un test di carico.

2. Espandere la cartella **Impostazioni di esecuzione**.

3. Fare clic con il pulsante destro del mouse sul nodo delle impostazioni esecuzione test che si vuole rendere attivo, quindi scegliere **Imposta come attivo**.

     Nell'**Editor test di carico** il nodo delle impostazioni esecuzione test interessato viene aggiornato con il suffisso "[Active]".

     L'impostazione di esecuzione test diventa attiva e rimane tale finché non se ne seleziona una diversa.

> [!NOTE]
> È possibile eseguire l'override dell'impostazione di esecuzione attiva impostando una variabile di ambiente denominata `Test.UseRunSetting=<run setting name>`. Questa funzione è utile quando si esegue un test di carico dalla riga di comando o da un file batch. Consente infatti di scegliere impostazioni di esecuzione diverse senza aprire il test di carico.

## <a name="specify-the-run-setting-to-use-from-the-command-line"></a>Specificare l'impostazione di esecuzione da usare dalla riga di comando

È possibile eseguire l'override delle impostazioni di esecuzione test predefinite nel test di carico impostando una variabile di ambiente dalla riga di comando:

**Set Test.UseRunSetting=PreProdEnvironment**

E per eseguire il test:

**mstest /testcontainer:loadtest1.loadtest**

## <a name="see-also"></a>Vedi anche

- [Configurare le impostazioni di esecuzione dei test di carico](../test/configure-load-test-run-settings.md)
- [Specifica degli insiemi di contatori e delle regole di soglia per i computer in un test di carico](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Procedura: Aggiungere altre impostazioni esecuzione test a un test di carico](../test/how-to-add-additional-run-settings-to-a-load-test.md)
