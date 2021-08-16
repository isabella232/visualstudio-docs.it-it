---
title: Accesso VBA per creare/aprire un progetto VSTO di sistema
titleSuffix: ''
description: Informazioni su come abilitare in modo esplicito l'accesso al Office di progetto VBA prima di poter creare o aprire un progetto Visual Studio Tools per Office di sistema.
ms.custom: seodec18, SEO-VS-2020
ms.date: 08/14/2019
ms.topic: conceptual
f1_keywords:
- vst.project.vbawrongversion
- VST.Project.VBASecurityGenericError
- VST.Project.VBASecurityPermissions
- VST.SelectDocWizard.MissingCOM
- VST.Project.VBASecurityNotSet
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e76aa3b3035a3c713c07ef56f67de393b6411cbac7d69bced415581eb0e2bd3d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121314732"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Abilitare l'accesso a VBA per creare o aprire un Strumenti di Visual Studio per il Microsoft Office di sistema

È necessario abilitare in modo esplicito l'accesso al sistema di progetto Visual Basic, Applications Edition (VBA) in Microsoft Office prima di poter creare o aprire un Strumenti di Visual Studio per il progetto Microsoft Office di sistema.

 Microsoft Office progetti di sviluppo richiedono l'accesso al sistema di progetto Visual Basic, Applications Edition (VBA) in Microsoft Office Word e Microsoft Office Excel, anche se i progetti non usano Visual Basic, Applications Edition. Il supporto in fase di progettazione dei controlli sia nei progetti di Visual Basic che in quelli di Visual C# dipende infatti dal sistema di progetto di Visual Basic, Applications Edition.

 Alcuni virus macro per Microsoft Office provano ad automatizzare il sistema di progetto di Visual Basic, Applications Edition per propagarsi. Abilitando l'accesso al sistema di progetto di Visual Basic, Applications Edition, si rimuove una protezione utile contro la diffusione dei virus macro. Rimangono tuttavia attivi i normali livelli di sicurezza delle macro, che, assieme all'elenco degli autori attendibili impostati per le applicazioni di Office, determineranno l'esecuzione delle macro nel computer.

> [!NOTE]
> Tale condizione si applica solo al computer di sviluppo. I computer degli utenti finali non necessitano di questa opzione abilitata per eseguire Office soluzioni.

 È importante notare che la disabilitazione dell'accesso al sistema di progetto di Visual Basic, Applications Edition non comporta da sola la protezione dai virus, ma consente semplicemente di interrompere la diffusione di alcuni virus ad altri documenti se il computer viene infettato da un virus macro. Per impostazione predefinita, l'opzione è disabilitata per fornire un ulteriore livello di sicurezza per il computer, ma la sua abilitazione non rende il computer maggiormente soggetto ai virus se si seguono le procedure di sicurezza consigliate.

 La protezione ottimale contro i virus macro di Office è l'esecuzione di Office a livello di sicurezza alto o molto alto, per considerare attendibili solo le macro provenienti da origini verificate e note e rimanere aggiornati con le patch di sicurezza e i programmi antivirus.

 È possibile abilitare o disabilitare l'opzione **Considera attendibile l'accesso Visual Basic Project** manualmente.

 È possibile ripristinare l'installazione di Office se vengono visualizzati errori VBA o COM.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Per abilitare o disabilitare l'accesso Visual Basic progetti

1. Scegliere la scheda **File** .

2. Fare clic su **Opzioni**.

3. Fare **clic su Centro protezione** e quindi su Centro protezione **Impostazioni**.

4. Nel Centro **protezione fare** clic su **Macro Impostazioni**.

5. Selezionare o deselezionare **Considera attendibile l'accesso** al modello a oggetti del progetto VBA per abilitare o disabilitare l'accesso Visual Basic progetti.

6. Fare clic su **OK**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Per abilitare o disabilitare l'accesso Visual Basic progetti con il sistema Microsoft Office 2007

1. Scegliere **Macro** dal menu Strumenti in Word o Excel **e** quindi fare clic su **Sicurezza**.

2. Nella finestra **di dialogo** Sicurezza fare clic sulla scheda **Autori attendibili** .

3. Selezionare questa opzione per abilitare o deselezionare l'opzione **Considera attendibile l'accesso Visual Basic Project**.

4. Fare clic su **OK**.

## <a name="to-set-your-office-macro-security-level"></a>Per impostare il livello di sicurezza delle macro di Office

1. Scegliere la scheda **File** .

2. Fare clic su **Opzioni**.

3. Fare **clic su Centro protezione** e quindi su Centro protezione **Impostazioni**.

4. Nel Centro **protezione fare** clic su **Macro Impostazioni**.

5. Nella sezione **Macro Impostazioni** selezionare l'impostazione desiderata.

6. Fare clic su **OK**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Per impostare il livello Office sicurezza macro con il sistema di Microsoft Office 2007

1. Scegliere **Macro** dal menu Strumenti in Word o Excel **e** quindi fare clic su **Sicurezza**.

2. Nella scheda **Livello di** sicurezza selezionare l'impostazione desiderata.

    La **scheda Livello di** sicurezza contiene informazioni dettagliate su ogni livello. Per altre informazioni, vedere l'argomento "Livelli di sicurezza delle macro" nella Guida di Office.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>Per installare VBA con Microsoft Office System 2007

1. In Pannello di controllo eseguire **Installazione applicazioni** o **Programmi e funzionalità**.

2. Selezionare Office **nell'elenco Programmi attualmente** installati.

3. Fare clic su **Cambia**.

4. Selezionare **Aggiungi o Rimuovi funzionalità** e quindi fare clic su **Continua.**

5. Selezionare **Scegliere la personalizzazione avanzata delle applicazioni** e quindi fare clic su **Avanti.**

6. Espandere **Office funzionalità condivise nell'elenco** Scegliere le opzioni di aggiornamento per applicazioni **e** strumenti.

7. Aprire il menu a discesa accanto a **Visual Basic, Applications Edition** e quindi fare clic su **Esegui da** Computer locale .

8. Fare clic su **Continue**.

9. Fare clic su **Chiudi**.

## <a name="to-repair-your-installation-of-office"></a>Per ripristinare l'installazione di Office

1. In Pannello di controllo eseguire **Installazione applicazioni** o **Programmi e funzionalità**.

2. Selezionare la versione di Office **nell'elenco Programmi attualmente** installati.

3. Fare clic su **Cambia**.

4. Selezionare **Reinstalla o Ripristina** e quindi fare clic su **Avanti.**

5. Selezionare **Rileva e ripristina errori nell'installazione Office** e quindi fare clic su **Installa**.

## <a name="see-also"></a>Vedi anche
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
