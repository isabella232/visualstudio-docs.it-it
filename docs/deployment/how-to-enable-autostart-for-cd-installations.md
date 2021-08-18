---
title: Abilitare l'avvio automatico per le installazioni da CD | Microsoft Docs
description: Informazioni su come abilitare l'avvio automatico quando si distribuisce un'ClickOnce per mezzo di supporti rimovibili, ad esempio CD-ROM o DVD-ROM.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: f16def763bebca4cc91b902d1f9202c6a6fdaede
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127922"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Procedura: Attivare l'avvio automatico per le installazioni da CD
Quando si distribuisce un'applicazione tramite supporti rimovibili, ad esempio CD-ROM o DVD-ROM, è possibile abilitare in modo che l'applicazione viene avviata automaticamente quando viene inserito il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `AutoStart` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] supporto.

 `AutoStart`può essere abilitato nella **pagina Pubblica** di progettazione **Project .**

### <a name="to-enable-autostart"></a>Per abilitare l'avvio automatico

1. Con un progetto selezionato in **Esplora soluzioni**, nel menu **Project** fare clic su **Proprietà**.

2. Fare clic sulla scheda **Pubblica**.

3. Fare clic sul pulsante **Opzioni** .

     Verrà **visualizzata la finestra di** dialogo Opzioni di pubblicazione .

4. Fare clic su **Distribuzione**.

5. Selezionare la casella **di controllo Per le installazioni da CD, avvia automaticamente il programma di installazione all'inserimento di CD.**

     Un file *Autorun.inf* verrà copiato nel percorso di pubblicazione quando viene pubblicata l'applicazione.

## <a name="see-also"></a>Vedi anche
- [Pubblicare applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Procedura: Pubblicare un'ClickOnce di pubblicazione usando la Pubblicazione guidata](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)