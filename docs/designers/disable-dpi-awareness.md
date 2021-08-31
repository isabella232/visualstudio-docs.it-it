---
title: Disabilitare la compatibilità con DPI in Visual Studio
description: Vengono illustrate le limitazioni di Progettazione Windows Form per i monitor HDPI e viene illustrato come eseguire Visual Studio come processo incompatibile con DPI.
ms.date: 08/30/2021
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.openlocfilehash: d56a3650f2dd8df2b314bd80b27b321a68a92a2e
ms.sourcegitcommit: 0c6cecf1b973a33003d924abeb382f23e62c134d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2021
ms.locfileid: "123230378"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Disabilitare la compatibilità con DPI in Visual Studio

Visual Studio è un'applicazione compatibile con DPI (Dots Per Inch) e ciò significa che lo schermo viene ridimensionato automaticamente. Se un'applicazione indica che non è compatibile con DPI, il sistema operativo la ridimensiona come bitmap. Questo comportamento è anche noto come virtualizzazione DPI. L'applicazione continua a pensare di essere in esecuzione con ridimensionamento al 100%, ovvero 96 dpi.

Questo articolo presenta le limitazioni di Progettazione Windows Form per i monitor HDPI e illustra come eseguire Visual Studio come processo incompatibile con DPI.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Progettazione Windows Form nei monitor HDPI

**Progettazione Windows Form** in Visual Studio non supporta il ridimensionamento. Ciò può causare problemi di visualizzazione quando si aprono alcuni moduli in **Progettazione Windows Form** con monitor HDPI (High Dots Per Inch). Ad esempio, i controlli possono essere visualizzati sovrapposti, come nell'immagine seguente:

![Progettazione Windows Form in un monitor HDPI](./media/win-forms-designer-hdpi.png)

Quando si apre un modulo in **Progettazione Windows Form** in Visual Studio con un monitor HDPI, Visual Studio visualizza una barra informativa gialla nella parte superiore della finestra di progettazione:

![Barra informativa in Visual Studio per il riavvio in modalità incompatibile con DPI](./media/scaling-gold-bar.png)

Il messaggio **ridimensionamento sullo schermo principale è impostato su 200% (192 dpi). Ciò potrebbe causare problemi di rendering nella finestra di progettazione.**

> [!NOTE]
> Questa barra informativa è stata introdotta in Visual Studio 2017 versione 15.8.

Se non si lavora nella finestra di progettazione e non è necessario modificare il layout del modulo, è possibile ignorare la barra informativa e continuare a lavorare nell'editor di codice o in altri tipi di finestre di progettazione. È anche possibile [disabilitare le notifiche](#disable-notifications) in modo che la barra informazioni non continui a essere visualizzata. Solo **l'Windows progettazione Form** è interessata. Se è necessario lavorare in **Progettazione Windows Form**, la sezione successiva include informazioni utili per [risolvere il problema](#to-resolve-the-display-problem).

## <a name="to-resolve-the-display-problem"></a>Per risolvere il problema di visualizzazione

Per risolvere il problema di visualizzazione sono disponibili tre opzioni:

- [Riavviare Visual Studio come processo incompatibile con DPI](#restart-visual-studio-as-a-dpi-unaware-process)
- [Aggiungere una voce del Registro di sistema](#add-a-registry-entry)
- [Impostare il ridimensionamento dello schermo su 100%](#set-your-display-scaling-setting-to-100)

> [!TIP]
> Se si preferisce gestire le impostazioni dalla riga di comando, accetta come parametro della riga di comando per l'esecuzione in modalità di ridimensionamento [`devenv.exe`](../ide/reference/devenv-command-line-switches.md) `/noscale` al 100%.

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Riavviare Visual Studio come processo incompatibile con DPI

È possibile riavviare Visual Studio come processo incompatibile con DPI selezionando l'opzione sulla barra informativa gialla. Questo è il modo migliore per risolvere il problema.

Quando Visual Studio viene eseguito come processo incompatibile con DPI, i problemi di layout della finestra di progettazione vengono risolti, ma i caratteri potrebbero apparire sfocati. Visual Studio viene visualizzato un messaggio informativo giallo diverso quando viene eseguito come processo inconsapevole di DPI che indica che Visual Studio è in esecuzione come processo inconsapevole **di DPI. Le finestre di progettazione WPF e XAML potrebbero non essere visualizzate correttamente.** La barra informativa offre anche l'opzione **Riavvia Visual Studio come processo compatibile con DPI**.

> [!NOTE]
> - In presenza di finestre degli strumenti non ancorate in Visual Studio quando viene selezionata l'opzione per il riavvio come processo incompatibile con DPI, la posizione di tali finestre degli strumenti potrebbe cambiare.
> - Se si usa il profilo di Visual Basic predefinito o se è stata deselezionata l'opzione **Salva nuovi progetti alla creazione** in **Strumenti** > **Opzioni** > **Progetti e soluzioni**, Visual Studio non è in grado di riaprire il progetto quando viene riavviato come processo incompatibile con DPI. È tuttavia possibile aprire il progetto selezionandolo in **File**  >  **Progetti e soluzioni recenti**.

È importante riavviare Visual Studio come processo compatibile con DPI quando non è più necessario lavorare in **Progettazione Windows Form**. Durante l'esecuzione come processo incompatibile con DPI, i caratteri possono essere sfocati e si potrebbero riscontrare problemi in altre finestre di progettazione, ad esempio la **finestra di progettazione XAML**. Se si chiude e si riapre Visual Studio mentre è in esecuzione in modalità incompatibile con DPI, diventa di nuovo compatibile con DPI. È anche possibile selezionare **l'opzione Riavvia Visual Studio come** processo in grado di riconoscere DPI nella barra informazioni.

### <a name="add-a-registry-entry"></a>Aggiungere una voce del Registro di sistema

È possibile contrassegnare Visual Studio come incompatibile con DPI modificando il Registro di sistema. Aprire l'**editor del Registro di sistema** e aggiungere una voce nella sottochiave **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers**:

**Voce:** a seconda che si usi Visual Studio 2017 o 2019, usare uno di questi valori:

- C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Se si usa l'edizione Professional o Enterprise di Visual Studio, sostituire **Community** con **Professional** o **Enterprise** nella voce. Sostituire anche la lettera di unità come necessario.

**Digitare**: REG_SZ

**Valore:** DPIUNAWARE

> [!NOTE]
> Visual Studio rimane in modalità incompatibile con DPI fino a quando non viene rimossa la voce del Registro di sistema.

### <a name="set-your-display-scaling-setting-to-100"></a>Impostare il ridimensionamento dello schermo su 100%

Per impostare il ridimensionamento dello schermo su 100% in Windows 10, digitare **impostazioni dello schermo** nella casella di ricerca della barra delle applicazioni e quindi selezionare **Cambia le impostazioni dello schermo**. Nella finestra **Impostazioni** impostare **Modifica la dimensione di testo, app e altri elementi** su **100%**.

L'impostazione del ridimensionamento dello schermo su 100% potrebbe non essere appropriata, perché può rendere l'interfaccia utente troppo piccola per essere utilizzabile.

## <a name="disable-notifications"></a>Disabilitare le notifiche

È possibile scegliere di non ricevere notifiche per i problemi di ridimensionamento DPI in Visual Studio. Ad esempio, potrebbe essere utile disabilitare le notifiche se non si lavora nella finestra di progettazione.

Per disabilitare le notifiche, scegliere  >  **Opzioni strumenti** per aprire la finestra di **dialogo** Opzioni. Scegliere quindi Windows **Generale di Progettazione** Form e impostare Notifiche di  >   **ridimensionamento DPI** su **False.**

![Opzione per le notifiche di ridimensionamento DPI in Visual Studio](./media/notifications-option.png)

Se si vogliono riabilitare le notifiche per il ridimensionamento in un secondo momento, impostare la proprietà su **True**.

## <a name="troubleshoot"></a>Risolvere problemi

Se la transizione per la compatibilità con DPI non funziona come previsto in Visual Studio, controllare se è presente il valore `dpiAwareness` nella sottochiave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** nell'editor del Registro di sistema. Se presente, eliminare il valore.

## <a name="see-also"></a>Vedi anche

- [Ridimensionamento automatico in Windows Form](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
- [Un'esperienza multi-monitor migliore con Visual Studio](https://devblogs.microsoft.com/visualstudio/a-better-multi-monitor-experience-with-visual-studio-2019/)
