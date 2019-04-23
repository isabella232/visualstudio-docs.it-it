---
title: 'Procedura dettagliata: Data binding nella finestra di progettazione XAML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner.DataBinding
ms.assetid: 1a99aeae-c3ef-407d-ba79-b8055489a43d
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a7a27b2744247bba78575b0387a958bda5990d8c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071616"
---
# <a name="walkthrough-binding-to-data-in-xaml-designer"></a>Procedura dettagliata: Data binding nella finestra di progettazione XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La finestra di progettazione XAML consente di impostare le proprietà di associazione dati tramite la tavola da disegno e la finestra Proprietà. Questa procedura dettagliata illustra come associare dati a un controllo. In particolare, la procedura dettagliata illustra come creare una classe di carrello semplice con una classe [DependencyProperty](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.dependencyproperty.aspx) denominata `ItemCount` e associare la proprietà `ItemCount` alla proprietà **Text** di un controllo [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx).  
  
### <a name="to-create-a-class-to-use-as-a-data-source"></a>Per creare una classe da utilizzare come origine dati  
  
1. Nel menu **File** , scegliere **Nuovo**, **Progetto**.  
  
2. Nella finestra di dialogo **Nuovo progetto** scegliere il nodo **Visual C#** o **Visual Basic**, espandere il nodo **Desktop di Windows** e scegliere il modello **Applicazione WPF**.  
  
3. Assegnare al progetto il nome **BindingTest** e fare clic sul pulsante **OK**.  
  
4. Aprire il file MainWindow.xaml.cs (o MainWindow.xaml.vb) e aggiungere il codice seguente. In C# aggiungi il codice nello spazio dei nomi `BindingTest` (prima delle parentesi di chiusura finali del file). In Visual Basic, aggiungere la nuova classe.  
  
    ```csharp  
    public class ShoppingCart : DependencyObject  
    {  
        public int ItemCount  
        {  
            get { return (int)GetValue(ItemCountProperty); }  
            set { SetValue(ItemCountProperty, value); }  
        }  
  
        public static readonly DependencyProperty ItemCountProperty =  
             DependencyProperty.Register("ItemCount", typeof(int),  
             typeof(ShoppingCart), new PropertyMetadata(0));  
    }  
  
    ```  
  
    ```vb  
    Public Class ShoppingCart  
        Inherits DependencyObject  
  
        Public Shared ReadOnly ItemCountProperty As DependencyProperty = DependencyProperty.Register(  
            "ItemCount", GetType(Integer), GetType(ShoppingCart), New PropertyMetadata(0))  
        Public Property ItemCount As Integer  
            Get  
                ItemCount = CType(GetValue(ItemCountProperty), Integer)  
            End Get  
            Set(value As Integer)  
                SetValue(ItemCountProperty, value)  
            End Set  
        End Property  
    End Class  
    ```  
  
     Questo codice imposta un valore 0 come numero predefinito dell'elemento usando l'oggetto [PropertyMetadata](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.propertymetadata.aspx).  
  
5. Scegliere **Compila**, **Compila soluzione** dal menu **File**.  
  
### <a name="to-bind-the-itemcount-property-to-a-textblock-control"></a>Per associare la proprietà ItemCount a un controllo TextBlock  
  
1. In Esplora soluzioni aprire il menu di scelta rapida per MainWindow.xaml e scegliere **Progettazione visualizzazioni**.  
  
2. Nella casella degli strumenti scegliere un controllo [Grid](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) e aggiungerlo al modulo.  
  
3. Dopo aver selezionato il controllo `Grid` fare clic sul pulsante **Nuovo** accanto alla proprietà **DataContext** nella finestra Proprietà.  
  
4. Nella finestra di dialogo **Seleziona oggetto** verificare che la casella di controllo **Mostra tutti gli assembly** sia deselezionata, scegliere **ShoppingCart** nello spazio dei nomi **BindingTest** e fare clic sul pulsante **OK**.  
  
     La figura seguente illustra la finestra di dialogo **Seleziona oggetto** con **ShoppingCart** selezionato.  
  
     ![Finestra di dialogo Seleziona oggetto](../designers/media/blendselectobject.PNG "BlendSelectObject")  
  
5. Nella **casella degli strumenti`TextBlock` scegliere un controllo**  e aggiungerlo al modulo.  
  
6. Dopo aver selezionato il controllo `TextBlock`, scegliere il marcatore della proprietà a destra della proprietà **Text** e scegliere **Crea associazione dati**. Tale marcatore ha l'aspetto di una piccola casella.  
  
7. Nella casella **Percorso** della finestra di dialogo Crea associazione dati scegliere la proprietà **ItemCount : (int32)** e fare clic sul pulsante **OK**.  
  
     La figura seguente illustra la finestra di dialogo **Crea associazione dati** con la proprietà **ItemCount** selezionata.  
  
     ![Finestra di dialogo Crea associazione dati](../designers/media/xaml-create-data-binding.png "xaml_create_data_binding")  
  
8. Premere F5 per eseguire l'app.  
  
     Il controllo `TextBlock` dovrebbe visualizzare il valore predefinito 0 come testo.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di un'interfaccia utente tramite la finestra di progettazione XAML](../designers/creating-a-ui-by-using-xaml-designer-in-visual-studio.md)   
 [NIB: Aggiungi finestra di dialogo convertitore di valori](http://msdn.microsoft.com/c5f3d110-a541-4b55-8bca-928f77778af8)
