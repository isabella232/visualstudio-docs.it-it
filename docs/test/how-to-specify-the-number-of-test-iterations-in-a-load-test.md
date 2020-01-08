---
title: Specificare il numero di iterazioni test in un'impostazione di esecuzione del test di carico
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, properties
- load tests, run settings
ms.assetid: 45a625db-b3e7-4d64-beda-b9a76248096d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 446da348c1a947e6c59b8ad60d9bd0799d0d4322
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75588941"
---
# <a name="how-to-specify-the-number-of-test-iterations-in-a-load-test-run-setting"></a>Procedura: Specificare il numero di iterazioni test in un'impostazione di esecuzione test di carico

Dopo avere creato il test di carico mediante la **Creazione guidata test di carico**, è possibile usare l'**Editor test di carico** per modificare le proprietà degli scenari in modo da soddisfare le necessità e gli obiettivi di test. Per altre informazioni, vedere [Procedura dettagliata: Creare ed eseguire un test di carico](../test/walkthrough-create-and-run-a-load-test.md).

Usando l'**Editor test di carico** è possibile modificare la proprietà **Iterazioni test** di un valore delle impostazioni esecuzione test nella finestra **Proprietà**. La proprietà **Iterazioni test** consente di specificare il numero di iterazioni da eseguire in tutti i test prestazioni Web e degli unit test in tutti gli scenari di un test di carico tramite l'**Editor test di carico**.

> [!NOTE]
> Per un elenco completo delle proprietà delle impostazioni di esecuzione test e delle relative descrizioni, vedere [Proprietà delle impostazioni di esecuzione test di carico](../test/load-test-run-settings-properties.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-specify-the-number-of-test-iterations-in-a-run-setting"></a>Per specificare il numero di iterazioni di test in un'impostazione esecuzione test

1. Aprire un test di carico.

     L'**Editor test di carico** viene visualizzato e mostra l'albero del test di carico.

2. Nell'albero del test di carico scegliere le impostazioni di esecuzione test nella cartella **Impostazioni di esecuzione**.

3. Scegliere **Finestra Proprietà** dal menu **Visualizza** per visualizzare le categorie e le proprietà delle impostazioni esecuzione test di carico.

4. Impostare la proprietà **Utilizza iterazioni test** su **True**.

5. Nella proprietà **Iterazioni test** immettere un numero che indica il numero di iterazioni di test da eseguire durante il test di carico.

6. Terminata la modifica della proprietà, scegliere **Salva** dal menu **File**. Sarà quindi possibile eseguire il test di carico usando il nuovo valore dell'opzione **Iterazioni test**.

## <a name="see-also"></a>Vedere anche

- [Configurare le impostazioni di esecuzione dei test di carico](../test/configure-load-test-run-settings.md)
- [Proprietà di uno scenario di test di carico](../test/load-test-scenario-properties.md)
