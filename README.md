# Leitor-de-Livros-com-Voz-e-MP3-TTS-IA-
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------

 Etapas para gerar o .exe com Launch4j
1. Compile o projeto Java
bash
Copiar
Editar
cd leitor-tts/src
javac -cp "caminho/do/freetts.jar" LeitorTTS.java
2. Crie um JAR
bash
Copiar
Editar
jar cfe leitor-tts.jar LeitorTTS LeitorTTS.class
Isso gera um leitor-tts.jar com o ponto de entrada na classe LeitorTTS.

3. Use o Launch4j
Abra o Launch4j GUI

Configure os seguintes campos:

Output file: leitor-tts.exe

Jar file: Caminho para leitor-tts.jar

Classpath: Adicione freetts.jar

JRE Minimum version: 17.0.0

Opcional: ícone .ico personalizado

Clique em Build Wrapper
