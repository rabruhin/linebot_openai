from azure.core.credentials import AzureKeyCredential
from azure.ai.language.questionanswering import QuestionAnsweringClient

endpoint = "https://ntshlanguage.cognitiveservices.azure.com"
credential = AzureKeyCredential("6efd0fe5897548f6af666c9b8d33e959")
knowledge_base_project = "ntshQA"
deployment = "production"

def main():
    client = QuestionAnsweringClient(endpoint, credential)
    with client:
        question="2月5日"
        output = client.get_answers(
            question = question,
            project_name=knowledge_base_project,
            deployment_name=deployment
        )
    print("Q: {}".format(question))
    print("A: {}".format(output.answers[0].answer))

if __name__ == '__main__':
    main()
