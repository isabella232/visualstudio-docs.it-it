---
title: Disabilitare la compatibilità con DPI in Visual Studio
description: Vengono illustrate le limitazioni di Progettazione Windows Form per i monitor HDPI e viene illustrato come eseguire Visual Studio come processo incompatibile con DPI.
ms.date: 04/05/2019
author: gewarren
ms.author: gewarren
manager: jillfra
ms.topic: conceptual
ms.openlocfilehash: fdcf255b8ad7c613a83284759a1f4859041acfc4
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/19/2019
ms.locfileid: "69619973"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Disabilitare la compatibilità con DPI in Visual Studio

Visual Studio è un'applicazione compatibile con DPI (Dots Per Inch) e ciò significa che lo schermo viene ridimensionato automaticamente. Se un'applicazione indica che non è compatibile con DPI, il sistema operativo la ridimensiona come bitmap. Questo comportamento è anche noto come virtualizzazione DPI. L'applicazione continua a pensare di essere in esecuzione con ridimensionamento al 100%, ovvero 96 dpi.

Questo articolo presenta le limitazioni di Progettazione Windows Form per i monitor HDPI e illustra come eseguire Visual Studio come processo incompatibile con DPI.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Progettazione Windows Form nei monitor HDPI

**Progettazione Windows Form** in Visual Studio non supporta il ridimensionamento. Ciò può causare problemi di visualizzazione quando si aprono alcuni moduli in **Progettazione Windows Form** con monitor HDPI (High Dots Per Inch). Ad esempio, i controlli possono essere visualizzati sovrapposti, come nell'immagine seguente:

![Progettazione Windows Form in un monitor HDPI](./media/win-forms-designer-hdpi.png)

Quando si apre un modulo in **Progettazione Windows Form** in Visual Studio con un monitor HDPI, Visual Studio visualizza una barra informativa gialla nella parte superiore della finestra di progettazione:

![Barra informativa in Visual Studio per il riavvio in modalità incompatibile con DPI](./media/scaling-gold-bar.png)

Il messaggio è il seguente: **Il ridimensionamento del display principale è impostato su 200% (192 dpi). Questa impostazione potrebbe causare problemi di rendering nella finestra di progettazione.**

> [!NOTE]
> Questa barra informativa è stata introdotta in Visual Studio 2017 versione 15.8.

Se non si lavora nella finestra di progettazione e non è necessario modificare il layout del modulo, è possibile ignorare la barra informativa e continuare a lavorare nell'editor di codice o in altri tipi di finestre di progettazione. È anche possibile [disabilitare le notifiche](#disable-notifications) in modo che la barra informativa non continui a essere visualizzata. Il problema interessa solo **Progettazione Windows Form**. Se è necessario lavorare in **Progettazione Windows Form**, la sezione successiva include informazioni utili per [risolvere il problema](#to-resolve-the-display-problem).

## <a name="to-resolve-the-display-problem"></a>Per risolvere il problema di visualizzazione

Per risolvere il problema di visualizzazione sono disponibili tre opzioni:

- [Riavviare Visual Studio come processo incompatibile con DPI](#restart-visual-studio-as-a-dpi-unaware-process)
- [Aggiungere una voce del Registro di sistema](#add-a-registry-entry)
- [Impostare il ridimensionamento dello schermo su 100%](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Riavviare Visual Studio come processo incompatibile con DPI

È possibile riavviare Visual Studio come processo incompatibile con DPI selezionando l'opzione sulla barra informativa gialla. Questo è il modo migliore per risolvere il problema.

Quando Visual Studio viene eseguito come processo incompatibile con DPI, i problemi di layout della finestra di progettazione vengono risolti, ma i caratteri potrebbero apparire sfocati. Visual Studio visualizza un messaggio informativo giallo diverso quando viene eseguito come processo incompatibile con DPI, ovvero **Visual Studio viene eseguito come processo incompatibile con DPI. È possibile che le finestre di progettazione WPF e XAML non vengano visualizzate correttamente.** La barra informativa offre anche l'opzione **Riavvia Visual Studio come processo compatibile con DPI**.

> [!NOTE]
> - In presenza di finestre degli strumenti non ancorate in Visual Studio quando viene selezionata l'opzione per il riavvio come processo incompatibile con DPI, la posizione di tali finestre degli strumenti potrebbe cambiare.
> - Se si usa il profilo di Visual Basic predefinito o se è stata deselezionata l'opzione **Salva nuovi progetti alla creazione** in **Strumenti** > **Opzioni** > **Progetti e soluzioni**, Visual Studio non è in grado di riaprire il progetto quando viene riavviato come processo incompatibile con DPI. Tuttavia, è possibile aprire il progetto selezionandolo in **File** > **Progetti e soluzioni recenti**.

È importante riavviare Visual Studio come processo compatibile con DPI quando non è più necessario lavorare in **Progettazione Windows Form**. Durante l'esecuzione come processo incompatibile con DPI, i caratteri possono essere sfocati e si potrebbero riscontrare problemi in altre finestre di progettazione, ad esempio la **finestra di progettazione XAML**. Se si chiude e si riapre Visual Studio mentre è in esecuzione in modalità incompatibile con DPI, diventa di nuovo compatibile con DPI. È anche possibile fare clic sull'opzione **Riavvia Visual Studio come processo compatibile con DPI** nella barra informativa.

### <a name="add-a-registry-entry"></a>Aggiungere una voce del Registro di sistema

È possibile contrassegnare Visual Studio come incompatibile con DPI modificando il Registro di sistema. Aprire l'**editor del Registro di sistema** e aggiungere una voce nella sottochiave **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers**:

**Voce**: a seconda che si stia usando Visual Studio 2017 o 2019, usare uno di questi valori:

- C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Se si usa l'edizione Professional o Enterprise di Visual Studio, sostituire **Community** con **Professional** o **Enterprise** nella voce. Sostituire anche la lettera di unità come necessario.

**Tipo**: REG_SZ

**Valore**: DPIUNAWARE

> [!NOTE]
> Visual Studio rimane in modalità incompatibile con DPI fino a quando non viene rimossa la voce del Registro di sistema.

### <a name="set-your-display-scaling-setting-to-100"></a>Impostare il ridimensionamento dello schermo su 100%

Per impostare il ridimensionamento dello schermo su 100% in Windows 10, digitare **impostazioni dello schermo** nella casella di ricerca della barra delle applicazioni e quindi selezionare **Cambia le impostazioni dello schermo**. Nella finestra **Impostazioni** impostare **Modifica la dimensione di testo, app e altri elementi** su **100%** .

L'impostazione del ridimensionamento dello schermo su 100% potrebbe non essere appropriata, perché può rendere l'interfaccia utente troppo piccola per essere utilizzabile.

## <a name="disable-notifications"></a>Disabilitare le notifiche

È possibile scegliere di non ricevere notifiche per i problemi di ridimensionamento DPI in Visual Studio. Ad esempio, potrebbe essere utile disabilitare le notifiche se non si lavora nella finestra di progettazione.

Per disabilitare le notifiche, scegliere **Strumenti** > **Opzioni** per aprire la finestra di dialogo **Opzioni**. Scegliere quindi **Progettazione Windows Form** > **Generale** e impostare **Notifiche per ridimensionamento DPI** su **False**.

![Opzione per le notifiche di ridimensionamento DPI in Visual Studio](./media/notifications-option.png)

Se si vogliono riabilitare le notifiche per il ridimensionamento in un secondo momento, impostare la proprietà su **True**.

## <a name="troubleshoot"></a>Risolvere i problemi

Se la transizione per la compatibilità con DPI non funziona come previsto in Visual Studio, controllare se è presente il valore `dpiAwareness` nella sottochiave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** nell'editor del Registro di sistema. Se presente, eliminare il valore.

## <a name="see-also"></a>Vedere anche

- [Ridimensionamento automatico in Windows Form](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)