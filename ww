#!/usr/bin/python3.8
import os,sys,random
PATH='/bin';EDYTOR='vim';folder='/skrypty'
def help():
	print(	u'''
		Menadżer skryptów użytkowych w systemie. Można skopiować inne pliki wykonywalne, nie tylko skomponowane w pythonie, ponieważ będzie załączany do wykonania interpreter.

	Parametry:
		-n    utworznie nowego rejestru
		-p    dodanie szablonu pythona w folderze z skryptami
		-d    próba usunięcia rejestru (tylko gdy istnieje skrypt o takiej samej nazwie w folderze skryptów)
		-e    edycja skryptu niekompilowalnego z folderu skryptów
		-r    uruchomienie skryptu
		-s    edycja kodu menadzera skryptów

	Rejestr ('''+PATH+''') nie jest tożsamościowy z skryptami ('''+PATH+folder+'''/)i można załączyć skompilowany plik w innym języku lub plik używający innego interpretera.


	Życzymy miłego użytkowania
	   DGE
''')
	exit()
szab2=\
u'''#!/usr/bin/python3.8
#wywołana zostanie funkcja main(), więc w niej zacznij umiesczać odwołania do funkcji
def main():
	pass # domyślnie nie wykonuje nic

'''
szab1=\
u'''#!/usr/bin/python3.8
def main():
	import sys,os
	os.system('ww -r '+sys.argv[0])
if __name__=='__main__':
	main()
'''
def ls(c=''):
	return os.listdir(PATH+c)
def se():
	os.system('sudo '+EDYTOR+' '+sys.argv[0])
def edit(name):
	if name==sys.argv[0]:
		if not 'n'==input(u'Chcesz edytować plik główny menadżera skryptów? [Y/n]'):
			os.system('sudo '+EDYTOR+' '+PATH+'/'+name)
	elif name in ls(folder):
		os.system('sudo '+EDYTOR+' '+PATH+folder+'/'+name)
	else:
		print(u'Wygląda na to, że nie ma takiego pliku który chcesz edytować. :/')
		if not 'n'==input(u'Może chcesz go stworzyć? [Y/n]'):
			print(u'Tworzę')
			python(name)
			print(u'Zrobione')
def create(name):
	if name in ls():
		print(u'Program wywoływany o tej nazwie już istnieje w folderze '+PATH+'!');quit()
	else:
		
		if False:
			os.system('sudo echo > '+PATH+'/'+name+'&& sudo chmod +x '+PATH+'/'+name+' && sudo chmod 777 '+PATH+'/'+name)
		
			with open(PATH+'/'+name,'w') as w:
				w.write(szab1)
		if True:
			os.system('sudo cp '+PATH+folder+'/szab1.ww '+PATH+'/'+name)
def remo(name):
	if name in ls(folder) and name in ls():
		os.system('sudo rm '+PATH+'/'+name)
	elif (not name in ls(folder)) and name in ls():
		rn=str(random.randint(1,4))
		if str(rn) == input(u'Upewnij się że to nie jest polecenie systemowe, ponieważ zostanie utracone bezpowrotnie. Wpisz następnie cyfrę '+rn+':  '):
			print(u'Usuwam...',end='')
			os.system('sudo rm '+PATH+'/'+name)
			print(u'\rUsunięto')
		else:
			print(u'Jak rozumiem nie chcesz tego usunąć :)')
	else:
		print(u'Najwidoczniej nie znajduje się tu odwołanie w rejestrze, które mógłbym usunąć :/')
def python(name):
	if name in ls(folder):
		a=input(u'Jakiś skrypt już istnieje w tym folderze, chcesz go zobaczyć? [Y/n]')
		if a=='n':
			return 0;
		else:
			edit(name)
	else:
		print(u'Kopiuję',end='')
		if False:
			os.system('sudo echo > '+PATH+folder+'/'+name+'&& sudo chmod +x '+PATH+folder+'/'+name)
			with open(PATH+folder+'/'+name,'w') as w:
				w.write(szab2)
		else:
			os.system('sudo cp '+PATH+folder+'/szab2.ww '+PATH+folder+'/'+name)
		print(u'\rZrobione')
		if not 'n'==input(u'Czy chcesz to edytować? [Y/n]'):
			edit(name)
		
def cat(name):
	if not name in ls(folder):
		print(u'Nie ma takiego pliku niestety w tym folderze.')
	else:
		os.system('cat '+PATH+folder+'/'+name)
def run(name):
	if not name in ls(folder):
		print(u'Nie ma najprawdopodobniej takiego skryptu w folderze, w którym powinny się one znajdować :/ ')
		if not 'n'==input(u'Może chcesz go utworzyć? [Y/n]'):
			print(u'Już się robi :3')
			python(name)
		return None
	
	os.system(PATH+folder+'/./'+name+' '+' '.join(sys.argv[3:]))
def main():
	if len(sys.argv)==1:
		print(u"Nie zdefiniowano dokładnie działania, użyj -h po więcej informacji.")
		quit()
	if len(sys.argv)==2 and (sys.argv[1]=='-n' or sys.argv[1]=='-r' or sys.argv[1]=='-e' or sys.argv[1]=='-p' or sys.argv[1]=='-d'):
		print(u'Źle podaneargumenty wywołąnia!');quit()
	elif len(sys.argv)>2:
		{'-e':edit,'-n':create,'-d':remo,'-p':python,'-r':run,'-cat':cat}[sys.argv[1]](sys.argv[2])
if __name__=='__main__':
	if sys.argv.count('-h'):
		help()
		exit()
	if sys.argv.count('-s'):
		se()
	main()
	


