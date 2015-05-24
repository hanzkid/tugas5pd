unit burhan_xitkj2_unit1;

{$mode objfpc}{$H+}

interface

uses
  Classes, SysUtils, db, FileUtil, Forms, Controls, Graphics, Dialogs, StdCtrls,
  DBGrids, Menus, ExtCtrls, ZConnection, ZDataset, Grids;

type

  { TForm1 }

  TForm1 = class(TForm)
    Button1: TButton;
    Button2: TButton;
    Button3: TButton;
    DataSource1: TDataSource;
    DBGrid1: TDBGrid;
    Label5: TLabel;
    MainMenu1: TMainMenu;
    MenuItem1: TMenuItem;
    Panel1: TPanel;
    Tambah: TButton;
    email: TEdit;
    Kelas: TEdit;
    Label1: TLabel;
    Label2: TLabel;
    Label3: TLabel;
    Label4: TLabel;
    Nama: TEdit;
    NIS: TEdit;
    ZConnection1: TZConnection;
    ZQuery1: TZQuery;
    ZQuery2: TZQuery;
    procedure Button1Click(Sender: TObject);
    procedure Button2Click(Sender: TObject);
    procedure Button3Click(Sender: TObject);
    procedure DBGrid1DrawColumnCell(Sender: TObject; const Rect: TRect;
      DataCol: Integer; Column: TColumn; State: TGridDrawState);
    procedure Label5Click(Sender: TObject);
    procedure MenuItem1Click(Sender: TObject);
    procedure NISKeyPress(Sender: TObject; var Key: char);
    procedure TambahClick(Sender: TObject);
  private
    { private declarations }
  public
    { public declarations }
  end;

var
  Form1: TForm1;

implementation

{$R *.lfm}

{ TForm1 }

procedure TForm1.TambahClick(Sender: TObject);
begin
  if nis.text = '' then
begin showmessage('NIS tidak boleh kosong'); nis.setfocus end
else if nama.text = '' then begin showmessage('Nama tidak boleh kosong'); nama.setfocus end
else if kelas.text = '' then begin showmessage('Kelas tidak boleh kosong'); kelas.setfocus end
else begin
  ZQuery2.SQL.clear;
  try
  ZQuery2.SQL.Add('insert into siswa values("'+nis.Text+'","'+nama.Text+'","'+kelas.Text+'","'+email.Text+'")');
  ZQuery2.ExecSQL;
  showmessage('Berhasil dimasukan');
  except
    showmessage('Gagal memasukan data. Periksa kembali!');
  end;
  ZQuery1.refresh;
end;
end;

procedure TForm1.Button1Click(Sender: TObject);
begin
  if  nis.text=''  then
begin
showmessage('Data harus diisi');
nis.setfocus;
end else
begin
    ZQuery2.SQL.Clear;
    try
    ZQuery2.SQL.Add('update siswa set NIS="'+nis.Text+'",Nama="'+nama.Text+'",Kelas="'+kelas.Text+'",email="'+email.Text+'" where NIS="'+nis.text+'"');
    ZQuery2.ExecSQL;
    except
      showmessage('Gagal dirubah. Pastikan  penulisan data!.     Data  NIS tidak bisa dirubah');
    end;
    showmessage('Berhasil dirubah');
    ZQuery1.Refresh;
end;
end;

procedure TForm1.Button2Click(Sender: TObject);
var
   QueryResult: Boolean;
  UserString: string;
begin
    if InputQuery('Hapus data', 'Masukan NIS', UserString)
  then
  begin  ZQuery2.SQL.Clear;
     try
     ZQuery2.SQL.Add('delete from siswa where NIS="'+UserString+'"');
     ZQuery2.ExecSQL;
     Showmessage('Berhasil dihapus');
     except
       showmessage('Gagal menghapus data. Periksa kembali!');
     end;
     ZQuery1.Refresh end
  else
  begin
  end
end;

procedure TForm1.Button3Click(Sender: TObject);
begin
   if MessageDlg('Konfirmasi', 'Anda yakin untuk keluar?', mtConfirmation,
   [mbYes, mbNo],0) = mrYes
  then Application.terminate;
end;

procedure TForm1.DBGrid1DrawColumnCell(Sender: TObject; const Rect: TRect;
  DataCol: Integer; Column: TColumn; State: TGridDrawState);
var
  grid : TDBGrid;
  row : integer;
begin
  grid := sender as TDBGrid;
  row := grid.DataSource.DataSet.RecNo;
  if row mod 2 = 1 then
     grid.Canvas.Brush.Color := clSilver
  else
     grid.Canvas.Brush.Color := clDkGray;
  grid.DefaultDrawColumnCell(Rect, DataCol, Column, State) ;
end;

procedure TForm1.Label5Click(Sender: TObject);
begin

end;

procedure TForm1.MenuItem1Click(Sender: TObject);
begin
  showmessage('Program  ini dibuat  oleh  burhan yusuf'+slinebreak+'Versi  2');
end;

procedure TForm1.NISKeyPress(Sender: TObject; var Key: char);
begin
  if not (Key in ['0'..'9', '.', #8, #9]) then
   begin nis.clear; showmessage('Harus Angka') end;
end;

end.

