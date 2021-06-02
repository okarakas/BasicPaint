unit paintp;
interface
uses
  forms, Controls,ComCtrls, StdCtrls, Classes,dialogs, ExtCtrls, ColorGrd,math;
type
  TForm1 = class(TForm)
    Panel1: TPanel;
    Rad: TRadioGroup;
    ColorGrid1: TColorGrid;
    TrackBar1: TTrackBar;
    procedure FormMouseDown(Sender: TObject; Button: TMouseButton;
      Shift: TShiftState; X, Y: Integer);
    procedure FormMouseUp(Sender: TObject; Button: TMouseButton;
      Shift: TShiftState; X, Y: Integer);
    procedure ColorGrid1Change(Sender: TObject);
    procedure TrackBar1Change(Sender: TObject);
    procedure FormMouseMove(Sender: TObject; Shift: TShiftState; X,
      Y: Integer);
    procedure FormCreate(Sender: TObject);
  private
  public
  end;
var
  Form1: TForm1;
  bas:boolean=false;
  xx,yy:integer;
implementation

{$R *.DFM}

procedure TForm1.FormMouseDown(Sender: TObject; Button: TMouseButton;
  Shift: TShiftState; X, Y: Integer);
begin
bas:=true;
form1.canvas.Ellipse(x-1,y-1,x+1,y+1);
xx:=x;
yy:=y;
end;

procedure TForm1.FormMouseUp(Sender: TObject; Button: TMouseButton;
  Shift: TShiftState; X, Y: Integer);
var k:integer;
begin
if bas then begin
case rad.ItemIndex of
1:begin
  form1.Canvas.MoveTo(xx,yy);
  form1.Canvas.LineTo(x,y);
  end;
2:Canvas.LineTo(x,y);
3:begin
  k:=min(abs(x-xx),abs(y-yy));
  form1.Canvas.Ellipse(xx,yy,xx+k,yy+k);
  end;
4:form1.Canvas.Ellipse(xx,yy,x,y);
5:form1.Canvas.Rectangle(xx,yy,x,y);
6:form1.Canvas.roundRect(xx,yy,x,y,15,15);
7:begin
  k:=(x-xx)div 2;
  form1.Canvas.Arc(xx,yy-k,x,y+k,xx,yy,x,y);
  end;
8:begin
  k:=abs(y-yy);
  canvas.Font.Size:=k;
  form1.canvas.Ellipse(x-1,y-1,x+1,y+1);
  Canvas.brush.Color:=colorgrid1.ForegroundColor;
  canvas.textout(xx,yy-(k div 2),inputbox('TEXT','Enter the text:',''));
  Canvas.brush.Color:=colorgrid1.backgroundColor;
  end;
end;
form1.canvas.Ellipse(x-1,y-1,x+1,y+1);
bas:=false;
end;
end;

procedure TForm1.ColorGrid1Change(Sender: TObject);
begin
form1.Canvas.Pen.Color:=colorgrid1.ForegroundColor;
form1.Canvas.brush.Color:=colorgrid1.backgroundColor;
end;

procedure TForm1.TrackBar1Change(Sender: TObject);
begin
form1.Canvas.Pen.Width:=trackbar1.Position;
end;

procedure TForm1.FormMouseMove(Sender: TObject; Shift: TShiftState; X,
  Y: Integer);
begin
if (bas)and(rad.ItemIndex=0)then begin
  form1.Canvas.MoveTo(xx,yy);
  form1.Canvas.LineTo(x,y);
  xx:=x; yy:=y;
end else if (bas)and(rad.ItemIndex=9)then begin
            form1.Canvas.MoveTo(xx,yy);
            form1.Canvas.LineTo(x,y);
            end;
end;

procedure TForm1.FormCreate(Sender: TObject);
begin
colorgrid1.ForegroundIndex:=11;
end;

end.

