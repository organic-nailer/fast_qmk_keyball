# QMK公式が提供する最新のCLI環境をベースにする
# これにより、ビルドに必要なツールチェーンが全て揃う
FROM qmkfm/qmk_cli:latest

# --- 開発用の非rootユーザー 'vscode' を作成 ---
# ホストOSとのファイルの所有権問題を回避し、セキュリティを向上させる
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# ユーザーとグループを作成し、sudo権限をパスワードなしで付与する
RUN groupadd --gid $USER_GID $USERNAME && \
    useradd --uid $USER_UID --gid $USER_GID -m $USERNAME && \
    apt-get update && \
    apt-get install -y sudo && \
    echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME && \
    chmod 0440 /etc/sudoers.d/$USERNAME

# 今後の操作を 'vscode' ユーザーで行う
USER $USERNAME
