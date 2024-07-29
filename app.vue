<template>
  <Head>
      <Title>AI Chat</Title>
  </Head>
  <div class="" style="width: 60vw; margin: 0 auto;">
    <!-- <NuxtRouteAnnouncer />
    <NuxtWelcome /> -->
    <!-- <NuxtPage /> -->
    <deep-chat
      style="border-radius: 10px; width: inherit; height: calc(100vh - 70px); font-size: 1.0rem; padding-top: 10px"
      v-if="isLoaded"
      :demo="false"
      :textInput="{ placeholder: { text: 'Text me something!' } }"
      :history="history"
      :connect='{
        "url": "http://localhost:8080/ai/conversation",
        "method": "POST"
      }'
    >
      <div
        style="
          width: 500px;
          background-color: #f3f3f3;
          border-radius: 10px;
          padding: 12px;
          padding-bottom: 15px;
          display: none;
        "
      >
        <div>
          <div style="text-align: center; margin-bottom: 8px; font-size: 16px">
            <h3>Chatbot Demo</h3>
            <div style="font-size: 15px; line-height: 20px">
              Chat với mô hình ngôn ngữ lớn (LLM) sử dụng custom tools để truy xuất những dữ liệu mang tính realtime và 
              RAG (Retrieval Augmented Generation) để truy xuất local data
            </div>
          </div>
        </div>
      </div>
    </deep-chat>
  </div>
</template>

<script lang="ts">
export default {
  async mounted() {
    
    if (import.meta.client) {
      // dynamically import the component and conditionally render it via isLoaded
      // when it has finished importing
      await import('deep-chat');
      this.isLoaded = true;
    }
  },
  data() {
    return {
      history: [
        // { role: 'user', text: 'Hey, how are you today?' },
        // { role: 'ai', text: 'I am doing very well!' },
      ],
      isLoaded: false,
    };
  },
};
</script>
