---
title: Accesso VBA per creare o aprire un progetto di sistema VSTO
titleSuffix: ''
description: Informazioni che è necessario abilitare in modo esplicito l'accesso al sistema di progetto di Office VBA prima di poter creare o aprire un progetto di Strumenti di Visual Studio per Office System.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62477f7cd37a7d5a416e8f42fb7eb2d2a8e43828
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846129"
---
# <a name="enable-access-to-vba-to-create-or-open-a-visual-studio-tools-for-the-microsoft-office-system-project"></a>Abilitare l'accesso a VBA per creare o aprire un Strumenti di Visual Studio per il progetto di sistema Microsoft Office

È necessario abilitare in modo esplicito l'accesso al sistema del progetto Visual Basic, Applications Edition (VBA) in Microsoft Office prima di poter creare o aprire una Strumenti di Visual Studio per il progetto di sistema Microsoft Office.

 Per i progetti di sviluppo Microsoft Office è necessario l'accesso al sistema del progetto Visual Basic, Applications Edition (VBA) in Microsoft Office Word e Microsoft Office Excel, anche se i progetti non utilizzano Visual Basic, Applications Edition. Il supporto in fase di progettazione dei controlli sia nei progetti di Visual Basic che in quelli di Visual C# dipende infatti dal sistema di progetto di Visual Basic, Applications Edition.

 Alcuni virus macro per Microsoft Office provano ad automatizzare il sistema di progetto di Visual Basic, Applications Edition per propagarsi. Abilitando l'accesso al sistema di progetto di Visual Basic, Applications Edition, si rimuove una protezione utile contro la diffusione dei virus macro. Rimangono tuttavia attivi i normali livelli di sicurezza delle macro, che, assieme all'elenco degli autori attendibili impostati per le applicazioni di Office, determineranno l'esecuzione delle macro nel computer.

> [!NOTE]
> Tale condizione si applica solo al computer di sviluppo. Per i computer degli utenti finali non è necessario abilitare questa opzione per eseguire soluzioni Office.

 È importante notare che la disabilitazione dell'accesso al sistema di progetto di Visual Basic, Applications Edition non comporta da sola la protezione dai virus, ma consente semplicemente di interrompere la diffusione di alcuni virus ad altri documenti se il computer viene infettato da un virus macro. Per impostazione predefinita, l'opzione è disabilitata per fornire un ulteriore livello di sicurezza per il computer, ma la sua abilitazione non rende il computer maggiormente soggetto ai virus se si seguono le procedure di sicurezza consigliate.

 La migliore protezione contro i virus macro di Office consiste nell'eseguire Office a un livello di sicurezza elevato o molto elevato, per considerare attendibili solo le macro provenienti da origini note e verificate e per rimanere sempre aggiornati sulle patch di sicurezza e sui programmi antivirus.

 È possibile abilitare o disabilitare l'opzione **trust Access per Visual Basic Project** manualmente.

 È possibile ripristinare l'installazione di Office se vengono visualizzati errori VBA o COM.

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-enable-or-disable-access-to-visual-basic-projects"></a>Per abilitare o disabilitare l'accesso ai progetti Visual Basic

1. Scegliere la scheda **File** .

2. Fare clic su **Opzioni**.

3. Fare clic su **Centro protezione**, quindi fare clic su **Impostazioni Centro protezione**.

4. Nel **Centro protezione** fare clic su **Impostazioni macro**.

5. Selezionare o deselezionare l' **accesso attendibile al modello a oggetti del progetto VBA** per abilitare o disabilitare l'accesso ai progetti Visual Basic.

6. Fare clic su **OK**.

### <a name="to-enable-or-disable-access-to-visual-basic-projects-with-the-2007-microsoft-office-system"></a>Per abilitare o disabilitare l'accesso ai progetti di Visual Basic con il sistema Microsoft Office 2007

1. Scegliere **macro** dal menu **strumenti** in Word o Excel, quindi fare clic su **sicurezza**.

2. Nella finestra di dialogo **sicurezza** fare clic sulla scheda **autori attendibili** .

3. Selezionare questa selezione per abilitare o deselezionare per disabilitare il **trust Access to Visual Basic Project**.

4. Fare clic su **OK**.

## <a name="to-set-your-office-macro-security-level"></a>Per impostare il livello di sicurezza delle macro di Office

1. Scegliere la scheda **File** .

2. Fare clic su **Opzioni**.

3. Fare clic su **Centro protezione**, quindi fare clic su **Impostazioni Centro protezione**.

4. Nel **Centro protezione** fare clic su **Impostazioni macro**.

5. Nella sezione **Impostazioni macro** selezionare l'impostazione desiderata.

6. Fare clic su **OK**.

### <a name="to-set-your-office-macro-security-level-with-the-2007-microsoft-office-system"></a>Per impostare il livello di sicurezza delle macro di Office con il sistema di Microsoft Office 2007

1. Scegliere **macro** dal menu **strumenti** in Word o Excel, quindi fare clic su **sicurezza**.

2. Nella scheda **livello di sicurezza** selezionare l'impostazione desiderata.

    La scheda **livello di sicurezza** contiene informazioni dettagliate su ogni livello. Per altre informazioni, vedere l'argomento "Livelli di sicurezza delle macro" nella Guida di Office.

### <a name="to-install-vba-with-the-2007-microsoft-office-system"></a>Per installare VBA con Microsoft Office System 2007

1. Nel pannello di controllo eseguire **Installazione applicazioni** o **programmi e funzionalità**.

2. Selezionare Office nell'elenco **Programmi attualmente installati** .

3. Fare clic su **Cambia**.

4. Selezionare **Aggiungi o Rimuovi funzionalità**, quindi fare clic su **continua**.

5. Selezionare **scegliere Personalizzazione avanzata delle applicazioni**, quindi fare clic su **Avanti**.

6. Espandere **funzionalità condivise di Office** nell'elenco **scegliere le opzioni di aggiornamento per le applicazioni e gli strumenti** .

7. Aprire il menu a discesa accanto a **Visual Basic, Applications Edition** e quindi fare clic su **Esegui da computer locale**.

8. Fare clic su **Continua**.

9. Fare clic su **Close**.

## <a name="to-repair-your-installation-of-office"></a>Per ripristinare l'installazione di Office

1. Nel pannello di controllo eseguire **Installazione applicazioni** o **programmi e funzionalità**.

2. Selezionare la versione di Office nell'elenco **Programmi attualmente installati** .

3. Fare clic su **Cambia**.

4. Selezionare **Reinstalla o Ripristina**, quindi fare clic su **Avanti**.

5. Selezionare **rileva e Ripristina errori nell'installazione di Office**, quindi fare clic su **Installa**.

## <a name="see-also"></a>Vedi anche
- [Soluzioni Office sicure](../vsto/securing-office-solutions.md)
