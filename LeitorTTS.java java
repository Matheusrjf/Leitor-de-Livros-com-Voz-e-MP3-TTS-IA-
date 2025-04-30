import com.sun.speech.freetts.*;

import java.io.*;

public class LeitorTTS {
    private static final String VOZ = "kevin16";

    public static void main(String[] args) {
        String caminhoArquivo = "livro.txt"; // Seu livro
        String texto = lerTextoDoArquivo(caminhoArquivo);
        if (texto == null || texto.isEmpty()) {
            System.out.println("Arquivo vazio ou não encontrado.");
            return;
        }

        System.out.println("Lendo livro com voz...");
        VoiceManager vm = VoiceManager.getInstance();
        Voice voice = vm.getVoice(VOZ);
        if (voice == null) {
            System.err.println("Voz não encontrada.");
            return;
        }

        voice.allocate();

        // Salvar como WAV
        try {
            AudioPlayer audioPlayer = new SingleFileAudioPlayer("voz", AudioFileFormat.Type.WAVE);
            voice.setAudioPlayer(audioPlayer);
            voice.speak(texto);
            audioPlayer.close();
            System.out.println("Arquivo voz.wav gerado.");
        } catch (Exception e) {
            e.printStackTrace();
        }

        voice.deallocate();

        // Converter para MP3 com LAME (opcional - linha de comando)
        try {
            Process process = Runtime.getRuntime().exec("lame voz.wav voz.mp3");
            process.waitFor();
            System.out.println("Arquivo voz.mp3 gerado com sucesso.");
        } catch (Exception e) {
            System.out.println("Erro ao converter WAV para MP3. Verifique se o LAME está instalado.");
        }
    }

    private static String lerTextoDoArquivo(String caminho) {
        try {
            return new String(java.nio.file.Files.readAllBytes(java.nio.file.Paths.get(caminho)));
        } catch (IOException e) {
            e.printStackTrace();
            return null;
        }
    }
}
