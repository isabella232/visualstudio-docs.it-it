---
title: Specificare il numero di iterazioni nell'impostazione esecuzione test di carico
description: Informazioni su come specificare il numero di iterazioni da eseguire su tutte le prestazioni Web e gli unit test in tutti gli scenari di un test di carico usando il Editor test di carico.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: fa7a2ef5c3f425a1b4bdd04021b07f3aea5a7739e930fb78af46b48d1d7573ad
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121268586"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Procedura: Specificare il numero di iterazioni test in un'impostazione di esecuzione test di carico

Dopo avere creato il test di carico mediante la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà degli scenari in modo da soddisfare le necessità e gli obiettivi di test. Per altre informazioni, vedere [Procedura dettagliata: Creare ed eseguire un test di carico](../test/walkthrough-create-and-run-a-load-test.md).

Usando il **Editor test di carico**, è possibile modificare la proprietà **Iterazioni test** di un valore delle impostazioni di esecuzione nella **finestra** Proprietà. La **proprietà Iterazioni** test specifica il numero di iterazioni da eseguire su tutte le prestazioni Web e gli unit test in tutti gli scenari di un test di carico **usando** l'Editor test di carico .

> [!NOTE]
> Per un elenco completo delle proprietà delle impostazioni di esecuzione e delle relative descrizioni, vedere [Proprietà delle impostazioni esecuzione test di carico](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Per specificare il numero di iterazioni di test in un'impostazione esecuzione test

1. Aprire un test di carico.

     L'**Editor test di carico** viene visualizzato e mostra l'albero del test di carico.

2. Nell'albero del test di carico scegliere le impostazioni di esecuzione test nella cartella **Impostazioni di esecuzione**.

3. Scegliere **Finestra Proprietà** dal menu **Visualizza** per visualizzare le categorie e le proprietà delle impostazioni esecuzione test di carico.

4. Impostare la proprietà **Utilizza iterazioni test** su **True**.

5. Nella proprietà **Iterazioni test** immettere un numero che indica il numero di iterazioni di test da eseguire durante il test di carico.

6. Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore dell'opzione **Iterazioni test**.

## <a name="see-also"></a>Vedi anche

- [Configurare le impostazioni di esecuzione dei test di carico](../test/configure-load-test-run-settings.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)
