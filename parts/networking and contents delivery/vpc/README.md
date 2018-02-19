# VPC
���[�U�[���w�肵�� CIDR �u���b�N������ Virtual Private Cloud (VPC) ���쐬���܂�

# �v���p�e�B
[�v���p�e�B](https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-vpc.html#w2ab2c21c10d469b9)

# �߂�l
�쐬���ꂽVPC�̘_��ID

# ��
~~~~
{
  "Mappings" : {
    "CloudFormationSettings" : {
      "S3" : {
        "TemplateDir" : "https://s3.us-east-2.amazonaws.com/cf-templates-j648jx7tgtus-us-east-2/"  
      }  
    }  
  },  
  "Resources": {  
    "VPCStack": {  
      "Type": "AWS::CloudFormation::Stack",  
      "Properties": {  
        "TemplateURL"     : { "Fn::Join": ["", [{ "Fn::FindInMap": [ "CloudFormationSettings", "S3", "TemplateDir"]},"vpc.json"]]}   
      }  
    }  
  }  
}  
~~~~
 