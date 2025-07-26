program ej1;
const
	dimF= 5;
Type
	subr2= 1..99;
	venta= record
		dia: integer;
		codP: integer;
		cantV: subr2;
	end;
	vectorVentas= Array [1..dimF] of venta;

procedure leerVenta (var v: venta);
begin
	write('Ingresar dia de venta: ');readln(v.dia);
	if (v.dia <> 0) then begin
		v.codP:= Random(14)+1;
		//write('Ingresar cantidad de productos vendida: ');readln(v.cantV);
		v.cantV:= Random(98)+1;
	end;
end;



procedure cargarVector (var vect: vectorVentas; var dimL: integer);
var
	ven: venta;
begin
	leerVenta(ven);
	while (ven.dia <> 0) AND (dimL < dimF)do begin
		dimL:= dimL+1;
		vect[dimL]:= ven;
		leerVenta(ven);
	end;
end;

procedure mostrarVector (vect: vectorVentas; dimL: integer);
var
	i:integer;
begin
	for i:= 1 to dimL do begin
		writeln('Dia: ',vect[i].dia);
		writeln('Codigo de producto: ',vect[i].codP);
		writeln('Cantidad vendida: ',vect[i].cantV);
		writeln('');
	end;
end;

procedure ordenacionInsercion (var v: vectorVentas; dimL: integer);
var
	j, i: integer; 
	aux: venta;
begin
	for i:= 2 to dimL do  begin
		aux:= v[i];
		j:= i-1;
		while (j > 0) and (v[j].codP > aux.codP) do begin
			v[j+1] := v[j];
			j:= j -1;
		end;
		v[j+1]:= aux;
	end;
end;

procedure eliminar (var v: vectorVentas; var dimL, cod1, cod2: integer);
var
	i, elementos: integer;
	pI, pF, min, min2: integer;
	enc, enc2: boolean;
begin
	if (cod1 < cod2)then begin
		min:= cod1;
		min2:= cod2;
		end
		else begin
			min:= cod2;
			min2:= cod1;
		end;
		i:= 1;
		enc:= false;
		enc2:= false;
		while (i < dimL)and (v[i].codP <= min2)do begin
			if (v[i].codP <= min) and (enc <> true)then begin
				if(v[i].codP = min)then
					pI:= i
				else
					pI:= i-1;
				enc:= true;
			if (v[i].codP >= min2)and (enc2 <> true)then begin
				if(v[i].codP = min2)then
					pF:= i
				end
				else if (v[i].codP > min2)then begin
						pF:= i-1;
						enc2:= true;
					end;
				end;
			i:= i+1;
		end;
		elementos:= pF - pI+1;
		for i:= pF+1 to dimL do begin
			v[pI]:= v[i];
			pI:= pI+1;
		end;
		dimL:= dimL - elementos;
		writeln('Se borraron: ',elementos,' elementos.');
end;

procedure armarNuevoV(v: vectorVentas; dimL: integer; var v2: vectorVentas; var dimL2: integer; var total: integer);
var
	i: integer;
begin
	for i:= 1 to dimL do begin
		if (v[i].codP MOD 2 = 0)then begin
			dimL2:= dimL2 +1;
			v2[dimL2]:= v[i];
			total:= total + v[i].cantV;
			end;
	end;
end;

procedure mostrarVector2(vect: vectorVentas; dimL: integer; total: integer);
begin
	mostrarVector(vect, dimL);
	writeln('El total de producto vendidos es: ',total);
end;

var
vec, vec2: vectorVentas;
dimL, dimL2, cod1, cod2, total: integer;
Begin
	dimL:= 0;
	dimL2:= 0;
	total:= 0;
	Randomize;
	cargarVector(vec, dimL);
	mostrarVector(vec, dimL);
	ordenacionInsercion(vec,dimL);
	mostrarVector(vec, dimL);
	write('Ingresar codigo 1: ');readln(cod1);
	write('Ingresar codigo 2: ');readln(cod2);
	eliminar(vec, dimL, cod1, cod2);
	mostrarVector(vec, dimL);
	armarNuevoV(vec,dimL, vec2, dimL2, total);
	mostrarVector2(vec2,dimL2, total);
end.
